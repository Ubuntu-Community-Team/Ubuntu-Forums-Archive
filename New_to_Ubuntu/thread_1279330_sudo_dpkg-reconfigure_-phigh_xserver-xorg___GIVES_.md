---
title: "sudo dpkg-reconfigure -phigh xserver-xorg   GIVES ERRORS PLEASE HELP"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by jaydubyaw on 2009-09-30
I recently installed Ubuntu 9.04 on an older laptop.  It seems like a fun system to use.  However, this OS doesn't seem to like my Intel 82815 video driver.  I have tried several fixes and have run into brick walls each time.  I have read sudo dpkg-reconfigure -phigh xserver-xorg will launch a GUI that will walk me thru adding 1024x768 to my options for video resolution.  I have seen it on the net in a lot of places.  I have copied and pasted from a lot of places into Terminal.  IT DOES NOT LAUNCH ANYTHING.  Instead, it gives this error...

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090930170820

I have tried various ways of deleting this file but it just comes back.  Could someone help me please?!?  I really need to be in 1024x768.  Thanks!

---

### Post by yeats on 2009-09-30
> I recently installed Ubuntu 9.04 on an older laptop. It seems like a fun system to use. However, this OS doesn't seem to like my Intel 82815 video driver.

You should read this: [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

There are solutions (not recommended for beginners, but if you are determined/desperate) here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

> I have read sudo dpkg-reconfigure -phigh xserver-xorg will launch a GUI that will walk me thru adding 1024x768 to my options for video resolution. I have seen it on the net in a lot of places. I have copied and pasted from a lot of places into Terminal. IT DOES NOT LAUNCH ANYTHING. 

Not sure where you read this, but all that command does is reset your /etc/X11/xorg.conf file to a basic generic configuration.

> Instead, it gives this error...

xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20090930170820

This is not an error - it's just warning you that the system is overwriting the existing xorg.conf file with the one that the command generates.  It is also letting you know where to find the file that was last there ("backup in /etc/X11/xorg.conf.20090930170820").

If you are truly a beginner at this, you might consider reinstalling with [Hardy]("http://releases.ubuntu.com/hardy/") (the LTS - Long Term Support release) or [Intrepid]("http://releases.ubuntu.com/8.10/") (supported through April of 2010) - they do not have the same problems with older Intel graphics as Jaunty does.

---

