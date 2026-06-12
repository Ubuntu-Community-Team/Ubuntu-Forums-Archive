---
title: "Problem in Using C/c++ under ubuntu."
date: 2010-07-30
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-30
Hi!
Well I am using ubuntu 10.04.
Recently I have installed c/c++ application, but while compiling programs I am getting error.

following is the program i tried to run....


#include<iostream.h>
#include<graphics.h>
#include<conio.h>
#include<math.h>
#include<dos.h>
#include<stdlib.h>
#include<stdio.h>
class lines
	{
	private:
	int length,x1,y1,x2,y2,x,y,dx,dy,wx,wy,w,width;
	public:
	lines();      //Constructor
	void showline();
	int sign(int);
	};

int lines::sign(int xx)
		{
		if(xx<0)
		return -1;
		if(xx==0)
		return 0;
		if(xx>0)
		return 1;
		return 0;
		}
lines::lines()
		{
		x=0;y=0;
		cout<<"
	"Enter The Co-Ordinates (x1,y1) ":=";
		cin>>x1>>y1;
		cout<<"
	"Enter The Co-Ordinates (x2,y2) ":=";
		cin>>x2>>y2;
		cout<<"
	"Enter The Width Of The Line ":=";
		cin>>width;
		}

void lines::showline()
		{
		char *s,*s1;
		if(abs(x2-x1)>=abs(y2-y1))
		length=abs(x2-x1);
		else
		length=abs(y2-y1);
		w=width;
		wx=((w-1)/2)*(sqrt((x2-x1)*(x2-x1)+(y2-y1)*(y2-y1))/abs(y2-y1));
		wy=((w-1)/2)*(sqrt((x2-x1)*(x2-x1)+(y2-y1)*(y2-y1))/abs(x2-x1));
		dx=(x2-x1)/length;
		dy=(y2-y1)/length;
		if(dy>dx)
		wy=wx;
		x=x1+0.5*sign(dx);
		y=y1+0.5*sign(dy);
		int i=1;
		setcolor(0);
		while(i<=length)
			{
			for(int j=0;j<wy;j++)
			putpixel((x+320),480-(y+240+j),6);
			for(j=0;j<wy;j++)
			putpixel((x+320),480-(y+240-j),6);
			putpixel((x+320),480-(y+240),6);
			x+=dx;
			y+=dy;
			i++;
			}
		setcolor(15);
		outtextxy(40,10,"The Points Are:=");
		sprintf(s,"A(%d,%d)",x1,y1);
		outtextxy(40,20,s);
		sprintf(s,"B(%d,%d)",x2,y2);
		outtextxy(40,30,s);
		getch();
		}
void main()
	{
	int gd=DETECT,gm,i,j,xx=240,xxx=380;
	clrscr();
	lines a;
	char *mess[]={"D","D","A"," ","A","L","G","O","R","I","T","H","M"};
	initgraph(&gd,&gm,"..\bgi");
	cleardevice();
	rectangle(120,40,320,240);
	rectangle(320,40,520,240);
	rectangle(120,240,320,440);
	rectangle(320,240,520,440);
	for(i=0,j=12;i<8,j>=6;i++,j--)
		{
		xx+=10;
		outtextxy(xx,10,mess[i]);
		xxx-=10;
		outtextxy(xxx,10,mess[j]);
		delay(100);
		}
	for(i=130;i<=510;i+=10)
		for(j=50;j<=430;j+=10)
		putpixel(i,j,15);
	for(i=130;i<=510;i+=10)
		{
		if(i==320)
		continue;
		outtextxy(i,237,"+");
		}
	for(i=50;i<=430;i+=10)
		{
		if(i==240)
		continue;
		outtextxy(317,i,"-");
		}
	outtextxy(310,230,"O");
	outtextxy(530,240,"X");
	outtextxy(320,450,"-Y");
	outtextxy(100,240,"-X");
	outtextxy(320,30,"Y");
	a.showline();
	closegraph();
	}




But i am getting error that I SUPPOSE I WOULD NOT GET IF THE SAME CODE I RUN AND COMPILE UNDER TURBO C/C++.....

following is the error:


amit@ubuntu:~$ sudo gedit line.c
amit@ubuntu:~$ cc -c line.c
line.c:1:21: error: iostream.h: No such file or directory
line.c:2:21: error: graphics.h: No such file or directory
line.c:3:18: error: conio.h: No such file or directory
line.c:5:16: error: dos.h: No such file or directory
line.c:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lines’
line.c:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
line.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
line.c:31:9: warning: missing terminating " character
line.c:31: error: missing terminating " character
line.c:32:37: warning: missing terminating " character
line.c:32: error: missing terminating " character
line.c:34:9: warning: missing terminating " character
line.c:34: error: missing terminating " character
line.c:35:37: warning: missing terminating " character
line.c:35: error: missing terminating " character
line.c:37:9: warning: missing terminating " character
line.c:37: error: missing terminating " character
line.c:38:34: warning: missing terminating " character
line.c:38: error: missing terminating " character
line.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
line.c: In function ‘main’:
line.c:81: error: ‘DETECT’ undeclared (first use in this function)
line.c:81: error: (Each undeclared identifier is reported only once
line.c:81: error: for each function it appears in.)
line.c:83: error: ‘lines’ undeclared (first use in this function)
line.c:83: error: expected ‘;’ before ‘a’
line.c:119: error: ‘a’ undeclared (first use in this function)
amit@ubuntu:~$ sudo gedit line.c
.
.
.
.

So I want to ask that If suppose i have to run c/c++ as one can run with turbo c/c++ then what should I need to do...?

thanks!

---

### Post by Paul820 on 2010-07-30
Hi, what you have there is a very old bit of code. The headers are all outdated and it is not even for ubuntu. graphics.h is an old Borland header file for do lines and things in a console window, conio.h is a windows header file (**con**sole **i**nput **o**utput). So you are not going to get it to compile on ubuntu i'm afraid. :(

The file is using cout and endl so all the header files should be like this
> #include<iostream>
#include<cmath>
#include<cstdlib>
That dos.h header file should have given you a clue ;)

---

