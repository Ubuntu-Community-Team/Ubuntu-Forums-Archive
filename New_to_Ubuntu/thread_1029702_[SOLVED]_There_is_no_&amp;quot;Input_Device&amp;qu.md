---
title: "[SOLVED] There is no &amp;quot;Input Device&amp;quot; section in xorg.conf"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-03
I'm trying to set SHMConfig to 'true' in /etc/X11/xorg.conf

I have done this before to enable the gsynaptics touchpad tool.

This morning I did a clean Intrepid install, was previously using Feisty.

But there is no "input device" section in my xorg.conf

Here is the contents of xorg.conf

----------------------------------
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

----------------------------------
I followed these instructions,
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)
but all it did was make my screen display more detailed and fancy.

How can I set SHMConfig to 'true' so that I can use gsynaptics?

I'm using a Dell Inspiron laptop, and I've used gsynaptics with Dapper and Feisty.

thanks

---

### Post by Nepherte on 2009-01-03
That is exactly the way you should do it and it should work too. The reason all the input devices are gone in xorg.conf is because since X.org 7.4, true input device hotplugging is enabled. fdi files are detected by hal and applied. Every input device section will be detected and replaced by hal. Are you sure you restarted hal (or rebooted as they suggest in the guide)?
```
sudo /etc/init.d/hal restart
```

---

### Post by MooseMagnet on 2009-01-03
That did it. Thank you. Thank you.
I thought I was to simply restart the machine.
I issued the command you sent, restarted the machine again, and it works.
Thank you.

---

