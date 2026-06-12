---
title: "start prog in dosemu"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-08-04
hi
I have got dosemu and want to run cm 9798 (championship manager 2) through it
however when I type CM2E16 <ENTER> (which is what the instructions should be) there is an error message
any idea how to start a prog in dosemu?
thanks

---

### Post by Sir Jasper on 2009-08-04
Hi,

If you recognize this picture:

[[img]http://a.imagehost.org/t/0654/DOSscreen.jpg[/img]](http://a.imagehost.org/view/0654/DOSscreen) 

Then note the file I want to run is in my Home directory, so
at the c:\> prompt on the bottom line I type ¨d:¨ (see 4th line from the bottom for the reason) then with slashes type the folder name, then the file name without its extension so d:\folder\file and press return.

My regards

PS Type the folder and file names exactly (upper and lower cases matter there).

---

### Post by Duke Togo on 2009-08-04
sir jasper
thanks for your help , which I am sure would have worked, but for some reason \ would not work in dosemu with my laptop
instead using the dosemu website I did:

sudo dosemu "/home/richard/cm9798/LAUNCH.EXE" in the terminal which thankfully worked
cheers

---

