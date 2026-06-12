---
title: "missing xorg.conf"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by garymlewis on 2009-03-31
I installed Ubuntu 8.10 server edition several months ago with a basic LAMP stack. No problems with daily use. No graphics interface but that was ok.  Today I installed the R statistics package. And now graphics becomes an issue (eg, to see output like charts, etc).

So I installed xserver-xorg, gdm and the open source Radeon driver, but /etc/X11/xorg.conf is empty (the file exists however). So I figure I've left out something important. And rather than plow ahead and really muck things up, I wonder if anyone can point me in the right direction. 

I do get the Ubuntu graphical login screen when the server starts up, and a small terminal window in the upper left of the screen after I log in. But I'm definitely doing something wrong here, so any help would be appreciated.

The graphics card is an ATI M22 [Mobility Radeon X300]. The box is an ThinkPad T43 that used to run Windows XP before I removed XP and installed Ubuntu 8.10. 

glxinfo | grep vendor shows SGI so the open source video driver seems to be installed ok.

Thanks!

---

### Post by Christmas on 2009-03-31
I don't have and ATI card, but maybe you can try:
```
sudo dpkg-reconfigure xserver-xorg
```
And follow the instructions.

---

### Post by khelben1979 on 2009-03-31
If you wish, you have the possibility to get the driver directly from the ATi website. Look [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English") (it's the 32 bit version).

---

### Post by Bruce M. on 2009-04-05
Yea, mine is a very small xorg.conf file compared to what it use to be, and I'm not totally happy about it.

Found out that xorg.conf isn't used any more, Ubuntu puts the information about you setup in RAM automatically now. Although if you put the setting back in xorg.conf it will read it as before. My problem is it isn't recognizing my keyboard properly nor my language selection I want.

Read about it here, a little 4 post thread: [How can Ubuntu not use xorg.conf?]("http://ubuntuforums.org/showthread.php?t=1111813&highlight=xorg.conf")

The xorg.conf is simple to edit compared to the new method, I also don't like the idea that Ubuntu now "assumes" what I want/need with my system.

Have a nice day.
Bruce

---

