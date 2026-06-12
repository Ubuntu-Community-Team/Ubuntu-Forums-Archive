---
title: "Help - Power LED on Broadcom-based Microsoft MN-720 802.11g wifi card"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by mx-5 on 2006-12-11
Newbie looking for help...

I was able to get this card working using ndiswrapper and wpa_supplicant with Ubuntu 6.06.  When Edgy came out, I decided to try an upgrade.  Tried to do it over wifi, but after that failed, I decided I'll just do a fresh install, except I'll try Xubuntu 6.10. (PIII 500 laptop with 320MB ram)

After installing Xubuntu over an internet connection (laptop doesn't have cd-rom, so I boot up with GRUB using linux and initrd and install over the laptop's built-in NIC), I couldn't get my wifi card to work.  The LEDs didn't behave the same (they appear to be off, but you can see a faint glow if you look closely).  The card is found if I look at lspci, or in Device Manager (although net.interface_up is false)  I've since reinstalled Ubuntu 6.10 (didn't like xfce), but I'm still seeing the same behavior.

The card itself works fine when I boot into WinXP.

And I'm hoping that I can setup this card in Edgy with WPA without needing to run ndiswrapper and wpa_supplicant.  I've read many howtos, but I can't find one definitive guide as everyone's doing something different...

Thanks.

---

### Post by mx-5 on 2006-12-13
Anyone?

---

### Post by FrodoB on 2006-12-13
If you did an upgrade you will have to reinstall ndiswrapper as the kernel modules are not transfered from one kernel to the next one you install I believe.

---

### Post by mx-5 on 2006-12-18
> **FrodoB said:**
> If you did an upgrade you will have to reinstall ndiswrapper as the kernel modules are not transfered from one kernel to the next one you install I believe.

I've deleted partition and reinstalled from scratch, and the MN-720 still appears to be non-functional in Edgy, while it works perfectly fine (LED brightly lit and flashing) in Windows XP.

I should be resolving this net.interface_up=false situation before proceeding, shouldn't I?

Thanks.

---

