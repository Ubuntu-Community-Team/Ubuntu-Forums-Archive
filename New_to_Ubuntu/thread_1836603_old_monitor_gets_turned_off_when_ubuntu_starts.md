---
title: "old monitor gets turned off when ubuntu starts"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by shevin on 2011-08-31
Guys my LCD monitor stopped working so I plugged my old TVM monitor (a CRT one)

the monitor works with windows Safemode but it doesnt work with Ubuntu 11.04 and doesn't work with Windows 7 normal mode either.

the monitor is fine until the ubuntu itself starts (after splash),the monitor gets turned off (the green LED of the monitor becomes Yellow)

I had nvidia proprietary driver .


[LIST=1]
[*]I tried to use ubuntu's recovery mode , and login using failed safe graphic but in failed safe , I just see the mouse pointer and it is not even has the menu when I Right click .
[*]I tried sudo dpkg-reconfigure xserver-xorg -phigh  but I got some errors like ike the version missing some digits ! or the digits in the begin of file are different with this version !
[*]I noticed in the ~/.config/monitor.xml there are resolutions and refresh rates that are too high for my Old-dated CRT monitor . I deleted monitor.xml , still no help.
[*]I tried ubuntu 10.10 live CD, the monitor doesn't work there either .
[/LIST]

 ... what should I do ? please someone help me out , I have a flight tomorrow and I need to copy some data on my ubuntu before my flight

---

### Post by Wim Sturkenboom on 2011-08-31
First of all, you should still be able to get to a console (e.g. <ctrl><alt><F1> where you can login and copy files.

Second, you probably have a utility called nvidia-xconfig. Try that.

---

### Post by mbuckingham24 on 2011-08-31
It sounds to me like your CRT is not supporting resolutions above a certain point, and enters "sleep" mode because it can't process the signal.  Windows safe mode boots to 640x480 (or maybe nowadays 800x600), therefore it displays for you.  Splash screens are often below this resolution.
Your CRT probably used to support higher resolutions, and thus reports to the OS that it can.  So the OS boots to a higher resolution after its splash screen.  Try telling your OS that you want to use 640x480, and if that works, move your way up (800x600, 1024x768, etc) until your display shuts off.

---

