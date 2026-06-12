---
title: "GNOME display manager hanging install?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Grayelve on 2008-12-15
Hello Ubuntu Fans  :popcorn:
   Have been trying this install about a half dozen times now only to have the system hang when checking the display manager as best I can figure. I am using the Ubuntu Live 810iso which has required restoring my winXP partition between installs. 
   So I get this popup saying "Display server has been shutdown about 6 time in the last 90 seconds. IT IS LIKELY THAT SOMETHING BAD IS GOING ON. Waiting 2 minutes before trying again on display :0."  I press enter to satisfy the OK so the window closes. 
   Here is the screen after the popup closes:
Starting GNOME display manager...
 Starting System Tools Backends system-tools-backends            OK
 Starting deferred execution scheduler atd                       OK
 Starting periodic command scheduler crond                       OK
 Enabling additional executable binary format binfmt-support     OK
 Checking battery state...                                       OK
This is how the screen stays as the popup keeps comming back every few minutes.
Tried 'shutdown' at this point but its in a loop and I have to power off and start over.
After thought, would 'syshalt' interupt the loop or some other command?

Think I need that alternate install disk I read about or a way to get to a command prompt to setup up a workable display senario. Crash read about linux is a must.
    Here is my system:
System mfg         VIA Technologies, Inc.
System model       VT8363
System type        X86-based PC
Processor          x86 Family 6 Model 6 Stepping 2 AuthenticAMD ~1529Mhz
BIOS Version/Date  Award 6.00 PG, 9/27/2001
SMBIOS Version     2.2

Video Adapter      NVIDIA GeForce FX 5500
Driver             nv4_mini.sys (6.14.10.9131) 1/18/2005

So ... Just wanted to say Hello to this forum and seek your help as to what is going on and how to get to a working install of Ubuntu.
Thanks in advance.
Just Grayelve

---

### Post by DieB on 2008-12-15
try it with the alternate install cd:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

p.s. from where u got this driver information?

---

### Post by Hospadar on 2008-12-15
I have in the past run ubuntu on a very similar system (video card that is) so I suspect you can get it to work.
As mentioned above, try the alternate desktop installer.  It installs the same system, but without requiring a graphical environment during the install.

---

### Post by Grayelve on 2008-12-15
DieB   Here is a link I saved:  [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/)
Hope it is of some help.
Just Grayelve

Thanks for the replys ... Will try alternate cd

---

### Post by DieB on 2008-12-15
are those in Hardware&Drivers not suiting yours?

---

