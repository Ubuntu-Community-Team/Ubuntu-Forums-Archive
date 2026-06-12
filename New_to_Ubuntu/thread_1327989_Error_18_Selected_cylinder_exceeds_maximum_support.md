---
title: "Error 18: Selected cylinder exceeds maximum supported by BIOS"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-16
Hey everyone,

My desktop computer powering my stereo crashed randomly (that's weird for Ubuntu!), and on the next boot, I got this message from GRUB:

> Error 18: Selected cylinder exceeds maximum supported by BIOS. Press ENTER to continue.

I pressed enter and it booted up just fine.

Is this the beginnings of a failing HDD? The drive is only 6 months old. 

I didn't change any settings in GRUB, nor have I made any system changes. 

Thanks for any help in advance!

---

### Post by 101011010010 on 2009-11-16
Hello there.
If your Dual-Booting there's an article on the Linux Questions Wiki, that explains the problem and how to fix it.
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18_on_Dual_Boot_Systems_Using_a_Single_Hard_Drive](http://wiki.linuxquestions.org/wiki/GRUB#Error_18_on_Dual_Boot_Systems_Using_a_Single_Hard_Drive)
I hope this helps.

---

### Post by asuastrophysics on 2009-11-16
i actually found that article earlier while searching around. the thing is though, i'm not dual booting. (well, not from a single hard drive anyway)

and the problem resolved itself. ubuntu booted successfully. 

I just didn't know if this was something I should be worried about (hard drive). it hasn't happened since then, it was just a one-time thing, which is why I was getting curious...  ;)

---

### Post by oldfred on 2009-11-16
If it is a newer computer I do not know why you got error 18.

Herman has good explanation of error 18 - see if any of the special cases he discusses  are like your setup.
[http://members.iinet.net/~herman546/p15.html#18](http://members.iinet.net/~herman546/p15.html#18)

---

### Post by asuastrophysics on 2009-11-19
> **oldfred said:**
> If it is a newer computer I do not know why you got error 18.

Herman has good explanation of error 18 - see if any of the special cases he discusses  are like your setup.
[http://members.iinet.net/~herman546/p15.html#18](http://members.iinet.net/~herman546/p15.html#18)

Thanks for your help. It hasn't happened since then, and I'm going to assume this was the result of installing updated packages before the shut down. 8-)

---

### Post by alsrmurad on 2010-07-14
> **asuastrophysics said:**
> Thanks for your help. It hasn't happened since then, and I'm going to assume this was the result of installing updated packages before the shut down. 8-)

if you using sata drive, try to replace sata cable, i was also facing this problem and i replaced sata cable with new one and it booted up normally.good luck.

---

