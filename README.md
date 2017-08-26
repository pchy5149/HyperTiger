SetBatchLines -1

Winmove,MapleStory,,0,0
CoordMode,Mouse,Relative

Gui, Add, Tab, x-1 y-1 w360 h240 , Setting1|Setting2
Gui, Tab, Setting1
Gui, Add, Text, x24 y52 w80 h20 , 아이템 이름
Gui, Add, Edit, x12 y29 w100 h18 vname, 
Gui, Add, Text, x144 y52 w80 h20 , 구매 가격
Gui, Add, Edit, x122 y29 w100 h18 vprice, 
Gui, Add, Text, x253 y52 w80 h20 , 구매 개수
Gui, Add, Edit, x232 y29 w100 h18 vnumber, 
Gui, Add, Text, x30 y112 w80 h20 , 판매 개수
Gui, Add, Edit, x12 y89 w100 h18 vsellnumber, 
Gui, Add, Text, x142 y112 w80 h20 , 판매 가격
Gui, Add, Edit, x122 y89 w100 h18 vsellprice,
Gui, Add, Text, x232 y112 w105 h20 , 딜레이(1000 = 1초)
Gui, Add, Edit, x232 y89 w100 h18 vdelay, 
Gui, Add, GroupBox, x12 y149 w330 h70 , F1:실행 F2:종료
Gui, Add, Button, x45 y169 w100 h40 , 저장
Gui, Add, Button, x207 y169 w100 h40 , 불러오기
Gui, Add, Text, x244 y149 w90 h18 , 제작:HyperTiger
Gui, Tab, Setting2
Gui, Add, Text, x24 y52 w80 h20 , 아이템 이름
Gui, Add, Edit, x12 y29 w100 h18 vname2, 
Gui, Add, Text, x144 y52 w80 h20 , 구매 가격
Gui, Add, Edit, x122 y29 w100 h18 vprice2, 
Gui, Add, Text, x253 y52 w80 h20 , 구매 개수
Gui, Add, Edit, x232 y29 w100 h18 vnumber2, 
Gui, Add, Text, x30 y112 w80 h20 , 판매 개수
Gui, Add, Edit, x12 y89 w100 h18 vsellnumber2, 
Gui, Add, Text, x142 y112 w80 h20 , 판매 가격
Gui, Add, Edit, x122 y89 w100 h18 vsellprice2, 
Gui, Add, GroupBox, x12 y149 w330 h70 , F1:실행 F2:종료
Gui, Add, Button, x45 y169 w100 h40 , 저장
Gui, Add, Button, x207 y169 w100 h40 , 불러오기
Gui, Add, Text, x244 y149 w90 h20 , 제작:HyperTiger
; Generated using SmartGUI Creator 4.0
Gui, Show, x151 y163 h233 w352, HyperTgier
Return

F1::
Gui,Submit,nohide
;검색 할 환경 만들기
s:=1
start:
ImageSearch,smX,smY,0,0,205,141, *30 검색메뉴.png ;sm=SearchMenu
If ErrorLevel=0
{
	MouseMove,181,121,0 ;검색 메뉴
	MouseClick,L,,,3
}

Sleep,%delay%

ImageSearch,csmX,csmY,0,0,110,720, *30 소비메뉴.png ;csm=Consumption Search Menu
If ErrorLevel=0
{
	csmX:=csmX+10
	MouseMove,%csmX%,%csmY%,0 ;소비 메뉴
	MouseClick,L,,,3
}

;검색 작업 시작
검색:
Loop
{ ;루프 시작
Loop,2
{
MouseMove,239,415,0 ;아이템 이름 입력
MouseClick,L
sendinput,{BS 10}
MouseClick,L,,,2
sendinput,{BS 10}
Clipboard=%name%
Clipwait
sendinput,{ctrl down}
Sleep,%delay%
sendinput,{v down}{v up}
sendinput,{ctrl up}
}

MouseMove,245,445,0 ;가격 입력
MouseClick,L
sendinput,{BS 10}
MouseClick,L,,,2
sendinput,{BS 10}
MouseMove,142,515,0 ;검색 시작 버튼
sendinput,%price%
MouseClick,L,,,8
MouseMove,987,230,0 ;검색후 첫번째 아이템 선택
sendinput,{Enter 5}
Sleep,%delay%
MouseClick,L
Sleep,%delay%

;검색 성공시
ImageSearch,srX,srY,263,143,341,179, *30 검색결과.png ;sr=Search Result
If ErrorLevel=0
{
	MouseClick,L,,,5
	MouseMove,948,714,0 ;구매하기 버튼
	MouseClick,L,,,10
	MouseMove,475,420,0 ;구매 개수
	MouseClick,L
	sendinput,{BS 5}
	MouseClick,L,,,2
	MouseMove,467,526,0 ;구매 확인
	sendinput,{BS 5}
	sendinput,%number%
	MouseClick,L,,,2
	break
}
;이미 판매 완료
ImageSearch,ascX,ascY,339,364,677,454, *30 이미판매완료.png ;Already sell Completion
If ErrorLevel=0
{
	Sendinput,{Enter 2}
}

;2번째 검색
검색2:
Loop,2
{
MouseMove,239,415,0 ;아이템 이름 입력
MouseClick,L
sendinput,{BS 10}
MouseClick,L,,,2
sendinput,{BS 10}
Clipboard=%name2%
Clipwait
sendinput,{ctrl down}
Sleep,%delay%
sendinput,{v down}{v up}
sendinput,{ctrl up}
}

MouseMove,245,445,0 ;가격 입력
MouseClick,L
sendinput,{BS 10}
MouseClick,L,,,2
sendinput,{BS 10}
MouseMove,142,515,0 ;검색 시작 버튼
sendinput,%price2%
MouseClick,L,,,8
MouseMove,987,230,0 ;검색후 첫번째 아이템 선택
sendinput,{Enter 5}
Sleep,%delay%
MouseClick,L
Sleep,%delay%

;검색 성공시
ImageSearch,srX,srY,263,143,341,179, *30 검색결과.png ;sr=Search Result
If ErrorLevel=0
{
	MouseClick,L,,,5
	MouseMove,948,714,0 ;구매하기 버튼
	MouseClick,L,,,10
	MouseMove,475,420,0 ;구매 개수
	MouseClick,L
	sendinput,{BS 5}
	MouseClick,L,,,2
	MouseMove,467,526,0 ;구매 확인
	sendinput,{BS 5}
	sendinput,%number2%
	MouseClick,L,,,2
	break
}
;이미 판매 완료
ImageSearch,ascX,ascY,339,364,677,454, *30 이미판매완료.png ;Already sell Completion
If ErrorLevel=0
{
	Sendinput,{Enter 2}
}
} ;루프 끝

;구매 성공
Loop
{ ;루프 시작
ImageSearch,sX,sY,412,370,582,450, *30 구매성공.png ;s=Success
If ErrorLevel=0
{
	If s>9
	{
	break
	}
	++s
	goto,검색
}
ImageSearch,ssX,ssY,352,371,674,449, *30 구매슬롯부족.png ;ss=Slot Shortage
If ErrorLevel=0
{
MouseMove,857,121,0 ;완료 메뉴
MouseClick,L,,,5
break
}
} ;루프 끝

Sleep,%delay%

;물품 수령
물품수령:
MouseMove,857,121,0 ;완료 메뉴
MouseClick,L,,,5
MouseMove,969,165,0 ;모두 받기 버튼
MouseClick,L,,,3
Sleep,%delay%
sendinput,{Enter}

Loop, 600
{ ;물품 수령 루프 시작
ImageSearch,rmX,rmY,308,344,717,475, *30 물품수령중.png ;rm=Receipt Massage
If ErrorLevel=0
{
	Sleep, 100
}
If ErrorLevel=1
{
ImageSearch,rsX,rsY,347,369,677,452, *30 물품수령완료.png ;rs=Receipt Success
IF ErrorLevel=0
{
	MouseMove,522,118,0 ;판매 메뉴
	MouseClick,L,,,10
	break
}
}
} ;물품 수령 루프 끝

Sleep,%delay%

;판매
sell:
ImageSearch,scmX,scmY,15,197,63,236, *30 판매소비메뉴.png ;scm=Sell Consumption Menu
If ErrorLevel=0
{
	MouseMove,42,218,0 ;판매 소비 메뉴
	MouseClick,L,,,3
}
ImageSearch,rdX,rdY,80,159,655,364, *30 빨간포션.png ;rp=Red Drug
If ErrorLevel=0
{
	MouseMove,%rdX%,%rdY%,0
	MouseClick,L
	MouseMove,844,254,0
	MouseClick,L
}

MouseMove,780,283,0 ;판매 개수
MouseClick,L,,,3
sendinput,%sellnumber%
Sleep,%delay%
MouseMove,946,284,0 ;개당 가격
MouseClick,L,,,3
sendinput,%sellprice%
MouseMove,940,347,0 ;판매 등록 버튼
MouseClick,L,,,3
Sleep,%delay%
sendinput,{Enter 5}
Sleep,%delay%

Loop
{ ;루프 시작
ImageSearch,sseX,sseY,348,366,680,453, *30 판매횟수초과.png ;sse=Sell Slot Exceed
If ErrorLevel=0
{
	Sendinput,{Enter 3}
	MouseMove,857,121,0 ;완료 메뉴
	MouseClick,L,,,5
	ImageSearch,arX,arY,916,148,1007,179, *30 모두받기.png ;ar=All Receive
	If ErrorLevel=0
	{
	goto,물품수령
	}
	MouseMove,522,118,0 ;판매 메뉴
	MouseClick,L,,,10
	MouseMove,975,471,0 ;X버튼
	Loop, 20
	{
	MouseClick,L,,,2
	Sleep,100
	}
	MouseMove,934,470,0
	Sleep,%delay%
	ImageSearch,scX,scY,964,462,986,483, *30 판매취소버튼.png ;sc=Sell Cancel
	If ErrorLevel=0
	{
	Loop, 10
	{
	MouseMove,975,471,0
	MouseClick,L,,,2
	Sleep,100
	}
	}
	goto,sell
}
If ErrorLevel=1
{
break
}
} ;루프 끝

;판매2
ImageSearch,qsX,qsY,80,159,655,364, *30 만병통치약.png ;qs=QuickSilver
If ErrorLevel=0
{
	MouseMove,%qsX%,%qsY%,0
	MouseClick,L
	MouseMove,844,254,0
	MouseClick,L
}

MouseMove,780,283,0 ;판매 개수
MouseClick,L,,,3
sendinput,%sellnumber2%
Sleep,%delay%
MouseMove,946,284,0 ;개당 가격
MouseClick,L,,,3
sendinput,%sellprice2%
MouseMove,940,347,0 ;판매 등록 버튼
MouseClick,L,,,3
Sleep,%delay%
sendinput,{Enter 5}
Sleep,%delay%

Loop
{ ;루프 시작
ImageSearch,sseX,sseY,348,366,680,453, *30 판매횟수초과.png ;sse=Sell Slot Exceed
If ErrorLevel=0
{
	Sendinput,{Enter 3}
	MouseMove,857,121,0 ;완료 메뉴
	MouseClick,L,,,5
	ImageSearch,arX,arY,916,148,1007,179, *30 모두받기.png ;ar=All Receive
	If ErrorLevel=0
	{
	goto,물품수령
	}
	MouseMove,522,118,0 ;판매 메뉴
	MouseClick,L,,,10
	MouseMove,975,471,0 ;X버튼
	Loop, 20
	{
	MouseClick,L,,,2
	Sleep,100
	}
	MouseMove,934,470,0
	Sleep,%delay%
	ImageSearch,scX,scY,964,462,986,483, *30 판매취소버튼.png ;sc=Sell Cancel
	If ErrorLevel=0
	{
	Loop, 10
	{
	MouseMove,975,471,0
	MouseClick,L,,,2
	Sleep,100
	}
	}
	goto,sell
}
If ErrorLevel=1
{
break
}
} ;루프 끝

s:=1
goto,start

button저장:
Msgbox,4,HyperTiger,정말 저장하시겠습니까?
IfMsgbox,No
return
gui,submit,nohide
filedelete save.ini
iniWrite,%name%,save.ini,Setting1,아이템 이름
iniWrite,%price%,save.ini,Setting1,구매 가격
iniWrite,%number%,save.ini,Setting1,구매 개수
iniWrite,%sellnumber%,save.ini,Setting1,판매 개수
iniWrite,%sellprice%,save.ini,Setting1,판매 가격
iniWrite,%delay%,save.ini,Setting1,딜레이
iniWrite,%name2%,save.ini,Setting2,아이템 이름
iniWrite,%price2%,save.ini,Setting2,구매 가격
iniWrite,%number2%,save.ini,Setting2,구매 개수
iniWrite,%sellnumber2%,save.ini,Setting2,판매 개수
iniWrite,%sellprice2%,save.ini,Setting2,판매 가격
msgbox,64,저장,완료
Return
button불러오기:
gui,submit,nohide
iniRead,내용저장1,save.ini,Setting1,아이템 이름
iniRead,내용저장2,save.ini,Setting1,구매 가격
iniRead,내용저장3,save.ini,Setting1,구매 개수
iniRead,내용저장4,save.ini,Setting1,판매 개수
iniRead,내용저장5,save.ini,Setting1,판매 가격
iniRead,내용저장6,save.ini,Setting1,딜레이
iniRead,내용저장7,save.ini,Setting2,아이템 이름
iniRead,내용저장8,save.ini,Setting2,구매 가격
iniRead,내용저장9,save.ini,Setting2,구매 개수
iniRead,내용저장10,save.ini,Setting2,판매 개수
iniRead,내용저장11,save.ini,Setting2,판매 가격
guicontrol,,name,%내용저장1%
guicontrol,,price,%내용저장2%
guicontrol,,number,%내용저장3%
guicontrol,,sellnumber,%내용저장4%
guicontrol,,sellprice,%내용저장5%
guicontrol,,delay,%내용저장6%
guicontrol,,name2,%내용저장7%
guicontrol,,price2,%내용저장8%
guicontrol,,number2,%내용저장9%
guicontrol,,sellnumber2,%내용저장10%
guicontrol,,sellprice2,%내용저장11%
Msgbox,64,불러오기,완료
return

F2::
Sendinput,{ctrl up}
exitapp
GuiClose:
ExitApp
