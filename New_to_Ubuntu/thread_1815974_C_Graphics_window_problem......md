---
title: "C Graphics window problem....."
date: 2011-08-01
forum: New to Ubuntu
---

### Post by vineesh314 on 2011-08-01
Rep: [IMG]http://lqcdn.thequestionsnetwork.net/questions/images/reputation/reputation_off.gif[/IMG]
 				 				    
 								 	 	 	 	 		 		 			 			 				[IMG]http://static.linuxquestions.org/questions/images/icons_lq/icon8.gif[/IMG] 				**C Graphics window problem.....** 			
 			 			 		 		  		  		#include<stdio.h>
#include<graphics.h>
void boundfil(int x, int y, int fill, int old)
{
if(getpixel(x,y)!=old && getpixel(x,y)!=fill)
	{
		putpixel(x,y,fill);
		boundfil(x+1,y,fill,old);
		delay(10);
		boundfil(x-1,y,fill,old);
		boundfil(x,y+1,fill,old);
		boundfil(x,y-1,fill,old);
	}
}

main()
{
int gd=DETECT,gm;
initgraph(&gd,&gm,"");
rectangle(100,200,450,400);
boundfil(101,201,5,15);
getch();
closegraph();
}

When I am trying to execute this progrm in Ubuntu the graphics window  comes and suddenly disposes when am trying to input the values..
and the error is.."a.out: ../../src/xcb_io.c:249: process_responses:  Assertion `(((long) (dpy->last_request_read) - (long)  (dpy->request)) <= 0)' failed.
Aborted
"
Anybody can help me..??
please.......

---

### Post by blind2314 on 2011-08-01
This would probably get more views, and subsequently more help, if moved or posted to the appropriate programming sub-forum.

---

### Post by vineesh314 on 2011-08-01
> **blind2314 said:**
> This would probably get more views, and subsequently more help, if moved or posted to the appropriate programming sub-forum.

This code well working in debian linux..
But not working in ubuntu...
The graphics window comes and suddenly disppears when trying to input...

vineesh@vineesh-M61PME-S2:~/c$ gcc ellipse1.c -lgraph
vineesh@vineesh-M61PME-S2:~/c$ ./a.out
a.out: ../../src/xcb_io.c:249: process_responses: Assertion `(((long)  (dpy->last_request_read) - (long) (dpy->request)) <= 0)'  failed.
Aborted

it is the error...........

---

### Post by vineesh314 on 2011-08-02
Actually the above code works well in my college system(debian linux).But when I tried it at home in my Ubuntu 10.10 pc,it is showing the error that i mentioned above...I am not really interested in installing Turbo C++ or any similar software to run it. anyway i shall install any additional libraries or edit any system files to make it work. Can anyone help me now..........???

---

### Post by vineesh314 on 2011-08-02
I installed all packages for the working of C Graphics like libgraph..
I did all things in my ubuntu system that i had done in debian linux....
The problem is regarding to ubuntu only...
please help me....

---

