---
title: "Inexplicable System Crash(es)"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by sharkllama on 2009-09-11
Hi There, 
   So i've recently run into some issues which cause my system to crash on a fairly regular basis and/or my mouse/keyboard to quit functioning.  I'm pretty much a newb here, but what I've done in the event that my system has crashed, or appears that it is about to crash, is to summon a virtual terminal and save the output of dmesg.  Say something like this:

$ dmesg > stall.txt

I've attached two dmesg outputs, one which occured when my mouse simply froze (and I tried resetting the usb hid driver to no avail) and the other when my system appeared to have crashed, but after waiting for quite a long time I was able to summon a virtual terminal.  Any insight into what is causing the problem, or how to regain control of my system is appreciated.  

*These issues tend to occur most frequently when I am using MATLAB and Banshee.

*The stall.txt file shows the dmesg output when the system appeared to stall and the mouseFail.txt file shows the dmesg output when the mouse was only frozen (still had my keyboard).

-Brant

---

### Post by Liolikas on 2009-09-11
Where those files are?

If possible try do not use MATLAB for some time still use Banshee others too. If no crash then reason is simple and very possible. 
MATLAB. This type of program tends to crash when too heavy calculations started. Try to use **maxima**. Also contact matlab support. What Linux can do just dump matlab well after hang.

---

### Post by sharkllama on 2009-09-11
Sorry About that, 
   Was fairly sure I had attached the files.  
-Brant

---

### Post by sharkllama on 2009-09-11
I fail to understand how MATLAB, which runs on top of the JRE could/should cause such a crash.  I would like to think that if anything got out of control that the Java Virtual Machine would catch the problem and terminate the process gracefully.  In either case I will be using MATLAB frequently, and I would like my computer to either completely execute the scripts or inform me that some error in my scripts caused the program to crash.  Simply hanging my machine is unacceptable...

Hopefully the dmesg outputs are readable to someone who understands them (I certainly don't) and we can troubleshoot the problem from there.  Thanks for you help in advance!
-Brant

---

