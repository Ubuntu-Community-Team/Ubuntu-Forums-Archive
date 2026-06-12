---
title: "Blinking Login after Fresh installed - tried a few things with no luck!!"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by linuxnoob53108 on 2010-04-24
So after a quick google search I have realized that this is a very  common issue, so I thought it would be an easy fix, that isn't turning out be very true unfortunately, and to complicate matters I'm trying to introduce my father to ubuntu since I have been so impressed and he hasn't exactly been won over yet because of this issue:

I did a fresh install from a flash drive of 9.10 onto the PC (HP Pavillion) and it went smooth, got the warning about proprietary drivers needing updated so I updated to 185 as it suggested. Rebooted and I got the blinking login screen of doom.

I restarted in recovery mode and edited my xconf file to use vesa as the driver. I rebooted and it works like a charm, but the screen resolution is only 800x600 which is totally lame.

I then found out that the nvidia card in the PC is a GeForce 6150 LE, so I went to nvidia's website and found the latest driver 195. So I downloaded the driver then rebooted again to a command line and installed the driver from following the on screen instructions. Still no luck.

Bottom line is that the 'nv' and 'vesa' drivers work fine, but I cannot get an nvidia driver to work. I'm tempted to just reinstall an older version because this is SOOOO frustrating, if anyone can help it would be much appreciated!

---

### Post by -humanaut- on 2010-04-24
I've had the same problem on two separate installs with the R.C. with nvidia cards (one Kubuntu another Ubuntu) try reinstalling the driver I've gotten that to work if it goes to TTY1 just wait a minute and gdm will boot up. I think it's because the Nouveau driver is built into the kernel instead of giving us the choice to choose.

---

### Post by Drate on 2010-04-24
[http://ubuntuforums.org/showthread.php?t=1306856](http://ubuntuforums.org/showthread.php?t=1306856)

See if anythign in that thread helps, if not, let us know what version of Ubuntu, what your video card is, or else give us the output of typing "sudo lspci" in a terminal.

And I had trouble with convertin my Dad because of the same sort of random issues, but he came around eventually.

---

### Post by -humanaut- on 2010-04-24
hitting ctrl+c at the TTY1 console seems to load KDM for me?

---

