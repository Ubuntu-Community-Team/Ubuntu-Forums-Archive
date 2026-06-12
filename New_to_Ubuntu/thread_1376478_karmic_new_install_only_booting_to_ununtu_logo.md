---
title: "karmic new install only booting to ununtu logo"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by d1g1tal on 2010-01-09
I've just installed 9.10 from a usb stick. The live version was looking ok, sounds worked, got wifi working. I did a full install and let it reboot, but now it only boots to an ubuntu logo. 

I can use ctrl alt del to get it to reboot and it seems to shut down properly if I press the power button (i.e. no need to hold it in) but I'm not sure what to do to force it to a command prompt or recovery mode to fix it.

I've rebooted it several times now once it said something like "one or more of the mount points cannot do blah blah - 
/lump waiting for null - press esc for recovery shell". I did that but it just showed the logo again then went to an "unsupported video mode" message from my monitor.

From the looks of things it might just be that the resolution it defaults to isn't support (I'm using a 42" LCT TV as my monitor - this is going to be my media centre box) but if I can't interrupt the startup I can't change it. 

If I boot from the usb again is there an easy way to change the default resolution from a config file? I'm pretty sure 1024 x 768 works OK.

Thanks

---

### Post by yeats on 2010-01-09
> I can use ctrl alt del to get it to reboot and it seems to shut down properly if I press the power button (i.e. no need to hold it in) but I'm not sure what to do to force it to a command prompt or recovery mode to fix it.

To get to a terminal, type Ctrl-Alt-F1 (actually F1 - F6 are virtual terminals) - to get back to the X session type Alt-F7.

Sounds like video, like you have suspected.  There is a file that *used* to control xorg settings, /etc/X11/xorg.conf, and it still might, but recent versions of Ubuntu have changed how that works...

---

### Post by d1g1tal on 2010-01-09
> **chrissharp123 said:**
> To get to a terminal, type Ctrl-Alt-F1 (actually F1 - F6 are virtual terminals) - to get back to the X session type Alt-F7.

Sounds like video, like you have suspected.  There is a file that *used* to control xorg settings, /etc/X11/xorg.conf, and it still might, but recent versions of Ubuntu have changed how that works...

Thanks for that Chris. Tried ctrl alt f1, but all that appeared to do was distort the logo and shift it to the bottom of the screen.

I had a look at xorg.conf but all it seemed to do was reference GDM, I couldn't see anything about screen setup there. I managed to find the gdm custom.conf file and remember how to open it as admin so that I could save it, then change autologin=true to autologin=false, but that hasn't made any difference.

Anything else I can try to boot into recovery mode or something else to get to a basic supported video mode?

Any help greatly appreciated.

---

### Post by yeats on 2010-01-09
This might be a useful read for you:

[http://ubuntuforums.org/showthread.php?t=1325212](http://ubuntuforums.org/showthread.php?t=1325212)

There are many tutorials on the Forums and on the web about setting up xorg.conf.  Good luck!

---

