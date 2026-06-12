---
title: "[SOLVED] driver install"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-06
Hi
I am trying to load this driver ,ati-driver-installer-8-12-x86.x86_64.run .
I have got as far as the ATI install panel .But the screen is so large I can't hit the next button as my display is locked in 800x600 .I have tried hitting the tab and enter ,but this will not work .Can someone help please .Thanks

---

### Post by Sef on 2009-01-06
Have you tried installing from System > Administration > Hardware Drivers?

---

### Post by marcgh on 2009-01-06
Hi,
I had exactly the same issue when  I was trying to install this same driver.
This is how I worked around:

Restart the computer and boot in safe mode.
From the list, select: reset Xserver, follow instructions and restart normally after that.
Now, you have a better resolution aloowing you to reach the 'bottom' of the ATI install frame.
Which GPU are you using? mine is a ATI Radeon 4850 and isworking perfectly now with Ubuntu.
Good luck!

---

### Post by garrydog on 2009-01-06
Hi 
This is the return from x -randr.david@david-desktop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
david@david-desktop:~$
The card I am using is ATI radeon HD 2400 pro .

---

### Post by marcgh on 2009-01-06
When I reset the Xserver ( see my previuos reply ) I got a resolution of 960 x 600. This was ok to install the driver.
did you reset the x driver?

---

### Post by garrydog on 2009-01-06
Hi
Booted in recovery mode ,then try to fix x server ,but i do not know what to do from there .Have booted in normal mode ,the screen is just the same .

---

### Post by marcgh on 2009-01-06
problem is, I am not at home and working under XP.
When I am back at home (2-3 hours time) I will check it out on my machine.

---

### Post by tarps87 on 2009-01-06
You can try holding alt and dragging the window off the top of the screen.
Note you will need to drag the windows from the middle not the top bar. Hope this makes sence.

---

### Post by garrydog on 2009-01-06
Hi Tarps87
That worked OK ,installed the driver ,no the resolution is OK .
Thanks very much .

---

