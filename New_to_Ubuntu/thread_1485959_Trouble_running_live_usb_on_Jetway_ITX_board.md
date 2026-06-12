---
title: "Trouble running live usb on Jetway ITX board"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by DancesWithRobots on 2010-05-17
I used unetbootin to create a bootable flash drive with NBR 10.04 on it.  When I allow it to start up with default settings, on most of the computers in the house, eventually I get to the Ubuntu desktop.

When I try to run it on an NF95A-270-LF mini ITX board,

 [http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=721&proname=NF95A-270-LF](http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=721&proname=NF95A-270-LF)

 I get to the purple screen with the scanning dots, and then after a  minute or so, the screen goes blank, and I get a display generated  message that means the screen can't display whatever it is it's getting.

If I give it a ctrl alt f1, I get to a terminal prompt, and an error message--"Your CPU appears to be lacking expected security protections" and a reference to NX setting in BIOS that I don't have.

I've also tried hitting "tab" at the unetbootin start screen and removing the "quietsplash" section, and adding "i915 modeset=1"  And I've tried creating a startup flash drive with the universal USB installer from pendrivelinux.com, and a few other flavors of ubuntu, but with no other success.

Like I said--I can get to a terminal prompt, but once I get there--I'm not quite sure where to go on.  Can someone walk me through some terminal level troubleshooting?

---

