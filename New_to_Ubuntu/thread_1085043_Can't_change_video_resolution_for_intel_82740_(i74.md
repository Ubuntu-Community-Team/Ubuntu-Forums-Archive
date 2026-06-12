---
title: "Can't change video resolution for intel 82740 (i740)"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by zvibez on 2009-03-02
Hi everyone, I'm very very new to ubuntu as I've just installed it and I have a problem with video settings.
I can't change video resolution for my video adapter (intel 82740 i740). I can only choose between 800x600, 640x480, 400x300... not 1024x768 for example...

I have read this thread [http://lists.freedesktop.org/mailman/listinfo/xorg]("http://lists.freedesktop.org/mailman/listinfo/xorg") but I'm not able to solve my problem.
This is my xorg.conf:

[FONT="Courier New"]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/FONT]

I've seen that in Synaptics I have the driver for my video adapter (see attachment) but what do I do with it? Perhaps I must install it? How do I do this? I don't know what to do, is there someone who can help me, please?
Many thanx!

---

