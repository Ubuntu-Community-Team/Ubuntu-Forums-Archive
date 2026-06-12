---
title: "ubuntu 9.10 and SiS: stuck at 800x600 screen resolution"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by ahoy-hoy on 2009-12-22
Hello,

I just installed Ubuntu 9.10 and my screen resolution is stuck at 800x600 with the only other option being 640x480. What I would like is a 1366x768. I saw that more people have this problem and tried different suggestions but nothing seems to work.

I am very new to Ubuntu and Linux in general so I don't really know what I am doing yet but want to learn. Excuse me if I ask ignorant questions.

what I  know: 
 xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

lspci |grep -i VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Can anyone please help me? My eyes are very unhappy.

ahoy-hoy

---

### Post by btedm on 2009-12-22
This seems to be a common problem.  Some monitors do not provide the information about resolution during the boot process.  Ubuntu then makes a safe assumption and uses a lower resolution than necessary.  The link [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)  gives suggestions for work arounds.

---

### Post by madnessjack on 2009-12-22
For me it's usually an issue with Ubuntu reading the monitor EDID (data about resolutions etc).

This tutorial has always got it working for me [http://ubuntuforums.org/showthread.php?t=316985](http://ubuntuforums.org/showthread.php?t=316985)

---

### Post by ahoy-hoy on 2009-12-22
> **madnessjack said:**
> For me it's usually an issue with Ubuntu reading the monitor EDID (data about resolutions etc).

This tutorial has always got it working for me [http://ubuntuforums.org/showthread.php?t=316985](http://ubuntuforums.org/showthread.php?t=316985)

thanks,
you know what to do if the phoenix EDID designer doesn't display any registry EDID
I go to tools>extract registry EDID>extract EDID and then it tells me Invalid EDID
Any idea what this means?

---

### Post by madnessjack on 2009-12-22
> **ahoy-hoy said:**
> thanks,
you know what to do if the phoenix EDID designer doesn't display any registry EDID
I go to tools>extract registry EDID>extract EDID and then it tells me Invalid EDID
Any idea what this means?
You need to select the EDID configuration that is being picked up by windows first. I'm at work at the minute and I can't remember the exact commands. But it's something like "select EDID config" from the file menu.

---

### Post by sujan01 on 2009-12-28
Is it possible that the monitor remains unknown during boot loading but it is known when the monitor power is set off and on?  See my posting at [http://ubuntuforums.org/showthread.php?p=8573812&highlight=screen+resolution#post8573812](http://ubuntuforums.org/showthread.php?p=8573812&highlight=screen+resolution#post8573812)

---

### Post by Onimishra on 2009-12-30
I have the same problem as the OP. The same hardware too. Been trying lots of different stuff over the last couple of days, and nothing works. xorg.conf, not working, nomodeset, not working.
This is where some Linux god, comes into play and says, try this this and this, and then it works :)

---

