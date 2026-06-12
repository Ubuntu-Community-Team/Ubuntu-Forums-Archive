---
title: "Install Advice Please"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by iscdriver on 2009-02-03
Hi all (New Member needing advice)

I am getting ready to install Abuntu on my PC.

I currently have Windows XP:p (a fresh Install) running on my computers Internal Hard Drive, and what I want to do is Install Abuntu on my USB External Hard Drive:D and then when I turn my computer on, I have the choice of which OS to run.

I know that you can install both to run along side each other and I know that you use the Grub to select which OS, but will this work with separate hard drives, especially with the setup I have.

If so how would I go about installing Abuntu onto my External drive, would I have to unplug my internal drive to install?

Your Help would be much appreciated.:D

---

### Post by sp0nge on 2009-02-03
I might be overlooking something here, but it seems to me that what your looking for will not be possible *exactly*..

Dual booting on one hard drive allows the MBR to see 2 operating systems on that disk. Since you can't boot both hard drives at once, you'll most likely have to change your BIOS settings to boot the external drive first then the internal drive after. This way, when the external drive is available, it will boot to that disk, and when it is not, the internal disk will take over.

If someone can show an alternative, I'd love to hear it. I have been experimenting with this for sometime myself.

---

### Post by Coreigh on 2009-02-03
To the best of my understanding the way to do this is install Ubuntu on the USB drive and when you want to "Choose" Ubuntu then you stick the drive in and to "choose" Windows you leave it out.

Also; am I missing something? Is there really and distro called "Abuntu" or is it just a typo / mis-understanding?

EDIT: After posting I thought about it a minute and began to wonder 'why couldn't you write your grub.conf (menu.1st) to look for a volume on a USB location?'

---

### Post by BDNiner on 2009-02-03
The only way i could see getting this done is to install ubuntu just like you would on a USB flash drive and then select what device to boot from using the BIOSes features.

---

### Post by iscdriver on 2009-02-03
Sorry Mis type in a way, my mind is not that quick ha ha.

---

### Post by iscdriver on 2009-02-03
I suppose I am asking a bit too much then. I do understand what you mean about changing the BIOS on 1st Boot options...I think that would be the only solution..

As for the install onto the Ext. drive, would I have to unplug my Int. drive first?

---

### Post by Coreigh on 2009-02-03
Install on the USB memory stick or external drive:

There is a special utility for this in 8.10. I think it is in the Applications menu.

---

### Post by iscdriver on 2009-02-03
Thanks Very Much

---

### Post by annda on 2009-02-03
> **iscdriver said:**
> I suppose I am asking a bit too much then. I do understand what you mean about changing the BIOS on 1st Boot options...I think that would be the only solution..

As for the install onto the Ext. drive, would I have to unplug my Int. drive first?

you don't have to unplug the internal HD drive, just make sure that while installing ubuntu you install the bootloader GRUB on the external drive - VERY IMPORTANT!

---

