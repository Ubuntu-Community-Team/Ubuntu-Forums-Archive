---
title: "Automatically boots into Terminal"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by knoelle on 2009-01-18
My sound suddenly stopped working in Linux last night and I was troubleshooting it to see if I could get it to work. I uninstalled the whole sound section and when I went to re-install it couldn't find the packages. I decided to reboot to see what would happen and when I did so it came up with the following. Literally booting into the terminal. I tried tty2-5 and they do the same thing. I'm at an utter loss and need help. This is what comes up when I load Ubuntu.

Thank you in advance for any help
-Karly



> Boot from (hd0,1) ext3 0bc9ec88-218e-46f1-bdb3-f3f3cc79f2ff
Starting up...
Loading, please wait...

Ubuntu 8.10 charlie-laptop tty1

charlie-laptop login: charlie
password:

Linux charlie-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:24:44 )38 2008 i686

The program included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright/

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To access official Ubuntu documentation, please visit [http://help.ubuntu.com/](http://help.ubuntu.com/)
charlie@charlie-laptop:~$]

---

### Post by Norm24 on 2009-01-18
Check this thread.I was able to resolve the same issue.

[http://ubuntuforums.org/showthread.php?t=1011010](http://ubuntuforums.org/showthread.php?t=1011010)

---

### Post by knoelle on 2009-01-18
ok great THANKS
 "startx" worked for me.

BUT it said

> The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

I didn't delete it because I figured I would ask first and I could go back and delete it if need be.

so yea...should I have deleted it?

---

