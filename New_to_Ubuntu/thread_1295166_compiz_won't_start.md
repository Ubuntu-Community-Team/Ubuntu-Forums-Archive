---
title: "compiz won't start"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by zorblek on 2009-10-19
I am using Jaunty with the latest updates on a Dell XPS M1210. When I log in, compiz doesn't start. This started after I had to do a hard reboot after a fullscreen Windows app running under wine caused the computer to freeze. I don't know if that has anything to do with it, but it seemed potentially relevent. When I try running compiz --replace from the command line, I get the following output:

Checking for Xgl: [username]:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

For some reason my screen resolution is incorrect as well, which is not usually the case when I use metacity.

I suspect that this is the same bug as [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/437805](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/437805) but I am not sure. (I have an Intel chipset, not Nvidia.)

Any help would be greatly appreciated.

---

### Post by K.Mandla on 2009-10-19
Have you seen this?

[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

Seems the intel driver had a few issues, which might include your card. There's a "fix," but no guarantees. ;)

---

### Post by zorblek on 2009-10-19
I believe that is for a different chipset (mine is i945GM). I tried it anyway. Compiz still won't start, but now I get the following output:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingSKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acq

---

### Post by zorblek on 2009-10-19
After enabling SKIP_CHECKS, I tried rebooting. When I logged into Gnome, all I got was a blank gray screen with a (movable) mouse arrow. Hitting Alt+Tab brought up the window switcher with the window icons of programs that run on startup, but no actual windows were displayed. After disabling SKIP_CHECKS and rebooting it went back to the previous behavior (Gnome started, but without compiz).

---

### Post by zorblek on 2009-10-20
I tried reinstalling xserver-xorg-video-intel. It didn't fix the problem, but afterward I got much more extensive output:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
damage_screen (XSR): 1 rects, bounds: 0,0 (1024,768)
expose_area (XSR): 1 rects, bounds: 0,25 (1,313)
expose_area (XSR): 1 rects, bounds: 735,25 (289,313)
expose_area (XSR): 1 rects, bounds: 0,338 (50,255)
expose_area (XSR): 1 rects, bounds: 360,338 (71,255)
expose_area (XSR): 1 rects, bounds: 735,338 (289,255)
expose_area (XSR): 1 rects, bounds: 0,593 (50,147)
expose_area (XSR): 1 rects, bounds: 360,593 (664,147)
expose_area (XSR): 1 rects, bounds: 0,740 (1024,27)
expose_area (XSR): 1 rects, bounds: 1,25 (49,313)
expose_area (XSR): 1 rects, bounds: 360,25 (71,313)
expose_area (XSR): 1 rects, bounds: 0,767 (1024,1)
expose_area (XSR): 1 rects, bounds: 0,0 (1024,1)
expose_area (XSR): 1 rects, bounds: 0,1 (50,24)
expose_area (XSR): 1 rects, bounds: 360,1 (71,24)
expose_area (XSR): 1 rects, bounds: 735,1 (289,24)
expose_area (XSR): 1 rects, bounds: 431,1 (304,592)
expose_area (XSR): 1 rects, bounds: 50,1 (310,739)
repair_win (XSR): 1 rects, bounds: 0,0 (1024,768)
configure notify 0 0 1
	extents (XSR): null
	xy (0 0), wh (1024 768)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,-7 (1042,786)
repair_win (XSR): 1 rects, bounds: -9,-7 (1042,786)
repair_win (XSR): 1 rects, bounds: -9,760 (1042,43)
repair_win (XSR): 1 rects, bounds: -9,-7 (1042,43)
configure notify 0 1 1
	extents (XSR): null
	xy (431 1), wh (306 619)
no extents to damage !
resize_win (XSR): 1 rects, bounds: 422,-6 (324,637)
configure notify 0 1 1
	extents (XSR): 1 rects, bounds: 422,-6 (324,637)
	xy (431 1), wh (306 619)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: 422,-6 (324,637)
configure notify 0 0 1
	extents (XSR): null
	xy (0 1), wh (1024 766)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,-6 (1042,784)
configure notify 0 0 1
	extents (XSR): 1 rects, bounds: -9,-6 (1042,784)
	xy (0 1), wh (1024 766)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-6 (1042,784)
configure notify 0 0 1
	extents (XSR): 1 rects, bounds: -9,-6 (1042,784)
	xy (0 1), wh (1024 766)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-6 (1042,784)
configure notify 0 0 1
	extents (XSR): 1 rects, bounds: -9,-6 (1042,784)
	xy (0 1), wh (1024 766)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-6 (1042,784)
configure notify 0 1 1
	extents (XSR): 1 rects, bounds: 422,-6 (324,637)
	xy (431 1), wh (306 619)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: 422,-6 (324,637)
configure notify 0 1 1
	extents (XSR): 1 rects, bounds: 422,-6 (324,637)
	xy (431 1), wh (306 619)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: 422,-6 (324,637)
repair_win (XSR): 1 rects, bounds: -109,-107 (19,19)
configure notify 1 0 1
	extents (XSR): 1 rects, bounds: -9,-7 (1042,786)
	xy (0 1), wh (1024 766)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-7 (1042,786)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
expose_area (XSR): 1 rects, bounds: 0,1 (1024,23)
expose_area (XSR): 1 rects, bounds: 436,1 (296,1)
expose_area (XSR): 1 rects, bounds: 434,2 (300,1)
expose_area (XSR): 1 rects, bounds: 433,3 (302,1)
expose_area (XSR): 1 rects, bounds: 432,4 (304,2)
expose_area (XSR): 1 rects, bounds: 431,6 (306,18)
expose_area (XSR): 1 rects, bounds: 431,24 (1,592)
expose_area (XSR): 1 rects, bounds: 736,24 (1,592)
expose_area (XSR): 1 rects, bounds: 431,616 (306,4)
repair_win (XSR): 1 rects, bounds: 422,-6 (324,637)
repair_win (XSR): 8 rects, bounds: 431,1 (306,619)
	434,2 (300,1)
	433,3 (302,1)
	432,4 (304,2)
	431,6 (306,18)
	431,24 (1,592)
	736,24 (1,592)
	431,616 (306,4)
repair_win (XSR): 1 rects, bounds: -9,-6 (1042,784)
repair_win (XSR): 1 rects, bounds: 189,768 (308,24)
repair_win (XSR): 3 rects, bounds: 24,768 (1000,24)
	497,768 (433,24)
	986,768 (38,24)
repair_win (XSR): 2 rects, bounds: 34,768 (952,24)
	956,768 (30,24)
repair_win (XSR): 1 rects, bounds: 0,1 (1007,766)
repair_win (XSR): 1 rects, bounds: 1007,1 (17,766)
repair_win (XSR): 1 rects, bounds: 1007,1 (17,766)
repair_win (XSR): 1 rects, bounds: 835,1 (22,22)
repair_win (XSR): 1 rects, bounds: 0,0 (1024,768)
repair_win (XSR): 1 rects, bounds: 0,0 (1024,768)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1007,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 858,1 (22,22)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1007,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)
repair_win (XSR): 1 rects, bounds: 0,1 (1024,766)

---

### Post by zorblek on 2009-10-20
I seem to have partially solved my problem. I'm not sure exactly what did it, but now at my screen resolution under metacity is correct. Here's what I did:

After reinstalling xserver-xorg-video-intel with no effect, I tried running "compiz.real --replace" instead of "compiz --replace" strangely, this seemed to actually get compiz to run, albeit in an unusable fashion. The screen resolution remained wrong, and all of my windows changed to strange sizes. I was unable to click on anything, although buttons still responded to being hovered over. I couldn't get anything to work, so I rebooted.

This time, when I logged into Gnome, compiz seemed to start properly. the resolution was correct, and everything worked as it should, with one exception: the interface was incredibly sluggish. For instance, I have my Gnome panels set to autohide. When I brought my mouse to the edge of the screen, nothing would happen. Then, 5 seconds or more later, the panel would show and then hide itself. Oddly, this sluggishness didn't seem to be caused by any particular process. htop showed no processes that were using a large amount of the CPU or RAM. And it only affected the graphical interface; I switched to a terminal, and everything there ran at a normal speed.

So I ran "metacity --replace", and it worked perfectly. The resolution was correct and the sluggishness gone. And now I can't get compiz to run again. I try, I get the following output:

Checking for Xgl: [username] not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1get fences failed: -1
param: 6, val: 0
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: get fences failed: -1
param: 6, val: 0
present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

I am completely baffled by this and would really like to get compiz working again.

---

