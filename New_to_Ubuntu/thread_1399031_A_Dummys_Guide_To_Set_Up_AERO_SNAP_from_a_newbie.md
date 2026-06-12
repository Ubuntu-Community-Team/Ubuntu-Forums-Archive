---
title: "A Dummys Guide To Set Up AERO SNAP from a newbie"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by verachion on 2010-02-05
I started using Ubuntu 9.10 yesterday, If your anything like me and not to familiar with the scripting heres a simple step by step guide to get aero snap up and running. 


[LIST]
[*]Open the Compiz Config Settings Manager (ALT+F2 ccsm, system > preferences > CompizConfig…, etc)
[*]Select the “Commands” option.
[*]In  'Command Line 0' paste: -
[/LIST]
 *WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1*


[LIST]
[*] In 'Command Line 1' paste: -
[/LIST]
 *WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1*


[LIST]
[*] And in 'Command Line 2' paste: -
[/LIST]
 *wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz*

It should now look something like this: -

[CENTER] [[IMG]http://4.bp.blogspot.com/_FJH0hYZmVtc/Svlh2yB1vAI/AAAAAAAAEXA/uVUsry_y9b4/s400/screenshot_020.png[/IMG]]("http://4.bp.blogspot.com/_FJH0hYZmVtc/Svlh2yB1vAI/AAAAAAAAEXA/uVUsry_y9b4/s1600-h/screenshot_020.png")
[/CENTER]
 
Now choose the 'Edge Bindings' tab at the top and set the following: -


[LIST]
[*]Run Command 0 - Set To Left
[*]Run Command 1 - Set To Right
[*]Run Command 2 - Set To Top
[/LIST]
 Click on the back button and go to 'General options'.

[CENTER] [[IMG]http://3.bp.blogspot.com/_FJH0hYZmVtc/SvlijUh2yvI/AAAAAAAAEXQ/o6RxXA1kNIY/s400/screenshot_022.png[/IMG]]("http://3.bp.blogspot.com/_FJH0hYZmVtc/SvlijUh2yvI/AAAAAAAAEXQ/o6RxXA1kNIY/s1600-h/screenshot_022.png")
[/CENTER]
 Set the  'Edge Trigger Delay' to something around 400 - 500 by dragging the slider to the right.

[CENTER] [[IMG]http://4.bp.blogspot.com/_FJH0hYZmVtc/SvliiDlMICI/AAAAAAAAEXI/xUm8GGcNyRM/s400/screenshot_023.png[/IMG]]("http://4.bp.blogspot.com/_FJH0hYZmVtc/SvliiDlMICI/AAAAAAAAEXI/xUm8GGcNyRM/s1600-h/screenshot_023.png")
[/CENTER]
 Now all you have to do is drag a window to one of the specified sides and your window will automatically resize.

This is not my guide I found it here [http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

---

### Post by monkeybanana on 2010-03-10
Hey there, I've tried this several times but it just won't work for me :(

I have Karmic installed on a new computer (Lenovo Thinkpad T400).

---

