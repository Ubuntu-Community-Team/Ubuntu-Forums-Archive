---
title: "Sound problems - again!"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by 99_rover on 2010-09-17
aaarrrrgggggggggg finally had everything working thanks to the upgrade help at

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

then ran upgrade manager today and now aplay -l shows no sound cards recognized however lspci -v shows my 

uname -a shows 
Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 2080 [size=64]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1

kernel is

Linux ubuntu 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

help!!!

---

### Post by davidmohammed on 2010-09-17
when you updated today - did it install a newer kernel?  Suggest use your grub (press shift when booting to display it) and select your older kernel to boot.  If your sound works, reboot into your newer kernel and reapply the fix you have found.

---

### Post by 99_rover on 2010-09-17
yep the upgrade introduced a new kernel - went back and recompiled the alsa drivers once again - now its working again

I hope I am not going to have to do this every time there is a kernel upgrade

---

