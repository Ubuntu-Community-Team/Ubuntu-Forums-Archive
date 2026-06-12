---
title: "openoffice menus unreadable after upgraded to 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by hl3613 on 2009-11-05
Greetings. 

Newbie here. Pardon my lack of linux knowledge please.

I used Update Manager to upgrade from 9.04 to 9.10. It went well, but something funky started to show up.

For OpenOffice.org, the menus and in-depth windows (for settings) became unreadable. (please see attached screenshots)

It happens to some, not all programs. EAC under WINE has the same problem too. 

Affected programs still function properly.

Under Language Support, I enable Chinese (Simplified and Traditional), but set the Menus and Windows at English.

My system: ThinkPad T40.

Any help is cordially welcome. If more info needed, please let me know. Thanks.

hl3613

---

### Post by squenson on 2009-11-05
Maybe it is the same issue as [http://ubuntuforums.org/showthread.php?t=1308943](http://ubuntuforums.org/showthread.php?t=1308943).

---

### Post by hl3613 on 2009-11-06
Thanks for helpful link. Problems look the same. But my situation improved (not fixed, because it still looks weird, see attachment, input areas show tiny blocks) after I came across Filesystem Failure and had to manually fcsk (?) to fix some errors. Now, Openoffice menus are readable, even though I did not uncheck the Screen Font Antialiasing. 

That said, EAC still has the same problem.

I am starting to suspect it's filesystem problem, or hd bad sector (nightmare).

---

### Post by SunnyRabbiera on 2009-11-06
Actually it looks more like a theme issue to me, or a graphics card issue.

---

### Post by hl3613 on 2009-11-07
Thanks for pointing at the right direction. I've solved the problem. It's indeed a display card issue. ThinkPad T40 has a Radeon card that does not fully support graphic acceleration which is turned on by default.  I followed the instruction and fixed the problems for good by editing /etc/X11/xorg.conf
(sort of EXA thing. Can't find the exact link now). Thanks again.

---

