---
title: "Everyone's Fav - Ndiswrapper Q's :)"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by tux_rox on 2007-06-15
After a succesfull installation of Feisty, I'm rearin' to go.  However, my wireless card (Microsoft Wireless Notebook Adapter MN-720 #2) is not recognized.  Since I basically can't do anything without internet, and I only have wireless internet in my house, I need to get this working.

I don't have the wireless cd, but I want to try ndiswrapper.  How do I get ndiswrapper working without the cd?  More importantly, how do I download ndiswrapper without internet?

Thanks in advance!

P.S.  Is ndiswrapper the only way to get support for wireless cards?

---

### Post by sct10 on 2007-06-15
NDISwrapper isn't needed for all wireless cards.  My old Lucent WaveLAN Turo card worked well without it but my Linksys card required it.  Then, after upgrading to Feisty my ndiswrapped Linsys card would no longer work.  If you can find an older card like my Lucent you might give that a try.  If you need to download ndiswrapper you'll have to get on a network somehow.

---

### Post by kevdog on 2007-06-15
Can you give me more specs about your wireless card.  Again ndiswrapper works for a lot of different cards, but not all, as stated by the previous poster.

Here's what I need
As much about the name of the card as you know -- is it USB, pcmcia, or pci slot interface?
At command line type at cut and paste the output in follow-up post.
lspci   <---if the card interfaces through pcmcia,or pci
lsusb  <----if its a USB card

---

### Post by ugm6hr on 2007-06-15
Card: Microsoft MN-720 80211g 54Mbps PCMCIA card - Broadcom Corporation BCM43xx, 80211b/g

    *
      Chipset: Broadcom 43xG (maybe a 4306?)
    *
      pciid: 14e4:4325 (rev 02) subsystem 1414:0003 Distro-specific: Gentoo 2.6.11-r4, ndiswrapper 1.1 ebuild (older: Gentoo 2.6.7-r11, Ndiswrapper 0.10 ebuild) (The older build, as of 8-22-2004, was not in portage tree - i’m still hosting it at [http://68.100.92.87:8080/ebuilds/ndiswrapper-0.10.ebuild](http://68.100.92.87:8080/ebuilds/ndiswrapper-0.10.ebuild) and [http://68.100.92.87:8080/ebuilds/files/ndiswrapper-0.10-modules.d](http://68.100.92.87:8080/ebuilds/files/ndiswrapper-0.10-modules.d) - honestly, you shouldn’t need to use this older build anymore, though)
    *
      Driver-and-Installation
    *
      *Option 1: Use a homegrown driver INF file that I have created, along with the same SYS file from above. It has the benefit that you will not have to create any symlinks. I’m hosting it for your convenience at [http://ankhcraft.com/drivers/mn720-ankh.zip](http://ankhcraft.com/drivers/mn720-ankh.zip) Please note that I do not provide any warranty for this INF file that I have created, express or implied. All I can say is that it works for me, and I’ve used this card heavily (with this driver).
    *
      *Option 2: Use Dell’s TrueMobile? 1300 driver. I’m hosting it for your convenience at [http://ankhcraft.com/drivers/bcmwl5.zip](http://ankhcraft.com/drivers/bcmwl5.zip) Please note that the pciids are not the same for this card, so, following driver installation into ndiswrapper, you’ll need to create some symlinks, like so (as root): ln -s 14e4:4320:1028:0002.conf /etc/ndiswrapper/14e4:4325:1414:0003.conf ln -s 14e4:4325:1414:0003.conf /etc/ndiswrapper/14e4:4325.conf
    *
      *Option 3: Use Microsoft’s driver from the cd (or optionally from [http://www.network-drivers.com/drivers/141/141400.htm](http://www.network-drivers.com/drivers/141/141400.htm)) Please be warned that this driver does not play nice with Linux hosted NDIS emulation wrappers in general. In order to get this driver work with ndiswrapper specifically, you must make sure you do NOT have the card plugged into the cardbus slot when you insert the ndiswrapper module. You’ll get a kernel panic if you do, and then you’re toast. Plug the card in afterward. After this, it works wonderfully. Also, it is worth mentioning that the Microsoft driver is known to be unstable when used with LinuxAnt’s driverloader. You may experience random system lockups, even though you may avoid the kernel panic mentioned above. I would suggest that you stay away from this driver under Linux. [email]joe@ankhcraft.com[/email] - ankhcraft


It looks like you have a Broadcom card (based on this from ndiswrapper wiki).  Unfortunately, this is notorious for being difficult to get working with Linux.  However, this does seem to suggest that it will work.  Best to check with:
```
lspci
```
to confirm the card.

---

### Post by tux_rox on 2007-06-15
Thanks for the responses - I'm going to try all of the above things until *something* works.

---

