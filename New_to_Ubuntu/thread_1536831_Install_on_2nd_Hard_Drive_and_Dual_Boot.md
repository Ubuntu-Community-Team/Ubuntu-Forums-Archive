---
title: "Install on 2nd Hard Drive and Dual Boot?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by jonvs on 2010-07-22
Hello:

This is probably a really easy question to answer, but it's been a long time since I've dealt with GRUB, or Linux in general, for that matter, and I'd like to get back into it.

My goal is to install either Ubuntu or Kubuntu 10.04 x64 on my machine alongside my existing Windows Vista x64 installation. I have two 80GB hard drives on this machine, the first of which carries my Windows install, and the second of which is completely empty. (The first hard drive is IDE, and the empty one is SATA, if that makes any difference.)

I started a Kubuntu installation. I was given the option of splitting my first drive, my IDE drive (which is about 75% full at this point), into two equal partitions, or to wipe another drive and install it on that. Both of my drives were strangely detected as being 100% full, so I had the feeling that some of my Windows files would be overwritten if I repartitioned my IDE drive. I also don't think I'd have enough space on that drive for a full installation, so that option doesn't make much sense. I would've chosen the second option, to wipe and use my secondary drive, but I'm worried that it will overwrite my boot record and my existing Windows installation will not be accessible, or perhaps the other way around.

My BIOS has a really easy-to-access boot menu, so I suppose I could  unplug my IDE drive temporarily, install Linux on the SATA drive, and plug it back in again. Would that be the best option?

Does anyone have any input about this? I'd appreciate some advice.

Thanks a lot!

---

### Post by mikewhatever on 2010-07-22
It sounds reasonable and is a pretty safe setup. Go for it!

---

### Post by Autodave on 2010-07-22
> **jonvs said:**
> Hello:


My BIOS has a really easy-to-access boot menu, so I suppose I could  unplug my IDE drive temporarily, install Linux on the SATA drive, and plug it back in again. Would that be the best option?

Does anyone have any input about this? I'd appreciate some advice.

Thanks a lot!

If you do that, I doubt that GRUB would ever recognize the Windows drive.  You would have to chose on your boot-up sequence every time to pick which OS you wanted to use.

---

### Post by jonvs on 2010-07-22
> **Autodave said:**
> If you do that, I doubt that GRUB would ever recognize the Windows drive.  You would have to chose on your boot-up sequence every time to pick which OS you wanted to use.

I think that's okay. I just wanted to make sure it'd work. I have to be vigilant every time I turn on my computer anyway, because my external hard drive needs to be turned off or my computer won't boot, but then it has to be turned back on before Windows finishes booting (long story). It wouldn't be that big of a deal to have to switch the boot device every time.

Thanks, guys!

---

### Post by oldfred on 2010-07-22
Either unplugging or not will work. If you do not unplug it will find windows when it sets up grub. But you have to be careful to install grub to the MBR of the Ubuntu drive and then set BIOS to boot it.

If you unplug the drive, run sudo update-grub and it should find windows and let you boot it. The issue with unplugging especially with mixed SATA & PATA drives is drive order may change and windows does not like that. Ubuntu usually will work around it.

See advanced button that lets you choose where grub is installed:
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

