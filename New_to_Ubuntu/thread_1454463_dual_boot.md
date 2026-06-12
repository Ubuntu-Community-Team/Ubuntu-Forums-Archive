---
title: "dual boot"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by godsmAsh on 2010-04-14
hi,
 how can i dual boot windows 7 and Ubuntu 10.04 beta 2?

 i've already installed windows 7 on my entire hard disk. 
 Then i've "shrink" the hard disk using disk management function in windows 7 but i'm not able to dual boot!!!
 when it boot it goes directly to windows 7.

 i've installed ubuntu first then windows 7.

---

### Post by cK` on 2010-04-14
I have been suggested to install windows first and then ubuntu ( somthing about windows loader being picky)

Do a fresh install of both, Install windows but do not take up the whole drive (I used half my drive for windows left the other half "unallocated") and then install ubuntu in the unallocated space.

---

### Post by coffeecat on 2010-04-14
> **godsmAsh said:**
> i've installed ubuntu first then windows 7.

That's your problem. Windows has overwritten grub stage 1 on the mbr with the Windows MBR. Rule-of-thumb: always install Windows first.

Anyway, have a look at section 13 (Reinstalling grub) in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You can find the same instructions at...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

... but there's something wrong with the help.ubuntu.com server today.

---

### Post by jaco223 on 2010-04-14
> **godsmAsh said:**
> hi,
 how can i dual boot windows 7 and Ubuntu 10.04 beta 2?

 i've already installed windows 7 on my entire hard disk. 
 Then i've "shrink" the hard disk using disk management function in windows 7 but i'm not able to dual boot!!!
 when it boot it goes directly to windows 7.

 i've installed ubuntu first then windows 7.


Did you install grub as the bootloader when you installed ubuntu?
You may have wiped ubuntu out when you installed windows
on the entire disk.

---

### Post by godsmAsh on 2010-04-15
i've followed the instruction on he following link and all is good now.


[http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista](http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista)

---

### Post by coffeecat on 2010-04-15
> **godsmAsh said:**
> i've followed the instruction on he following link and all is good now.


[http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista](http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista)

Your original question was about dual-booting Windows 7 and Ubuntu and getting Ubuntu to boot, but that link is a howto for dual-booting Windows 7 with Vista or XP. :confused:

---

### Post by barney385 on 2010-04-15
Here it is:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by godsmAsh on 2010-04-15
> **coffeecat said:**
> Your original question was about dual-booting Windows 7 and Ubuntu and getting Ubuntu to boot, but that link is a howto for dual-booting Windows 7 with Vista or XP. :confused:


thanks.. it's an error :)

here's the link:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by coffeecat on 2010-04-15
> **barney385 said:**
> Here it is:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I was more interested to know how the OP managed to get Ubuntu booting with the link they posted. :wink:

**edit:** ah, I see the OP did use the correct link.

@godsmAsh, I'm glad you've got it working. Those Lifehacker articles look good. Worth knowing about. :)

---

### Post by barney385 on 2010-04-15
> **coffeecat said:**
> I was more interested to know how the OP managed to get Ubuntu booting with the link they posted. :wink:

Yeah...I'm more inclined to follow an in-house(Ubuntu) support page/info...

---

