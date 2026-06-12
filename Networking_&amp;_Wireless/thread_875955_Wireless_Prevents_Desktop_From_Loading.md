---
title: "Wireless Prevents Desktop From Loading"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by ozanamn on 2008-07-31
Hi all 

Just wondering if someone could help me out. I installed ubuntu hardy 7.04 and my wireless never worked even with ndiswrapper. When the upgrade came out it was great i got my wireless working, But when i reset i got the gnome setting demon error that alot of people have been getting and iv looked thru alot of forums and tried a lot of different stuff and nothing had worked. When i take my wireless card out i boot up and delete the driver from ndiswrapper and reboot and put the wireless card back in. 

The PC boots up fine and i add the driver again and everything works fine. I just have to keep deleting the driver every time i turn the computer off which i was fine with until i turned it on and and then the ndiswrapper GUI wouldn't load up and i couldn't add the driver.

So i figured it being a Gnome setting demon error ill try xfce as its meant to be faster. It was faster but it wouldn't boot up either i wouldn't get an error message id log in and the desktop wouldn't load. 

So i have went back to gnome and reinstalled ubuntu fresh and am back to the start with deleting the driver and reinstalling it and I'm just waiting for the ndiswrapper to fail on me again. 

I also have a AH2600 HD graphics card that no matter how hard i try just will not work on ubuntu. I have tried a few different drivers and to no avail and have had to reinstall a fresh copy of ubuntu as the screen would go black even when i boot in safe mode and try to FIX Xserver but that screen is black two. 

I dont mean to be repeating any forums but i have tried a few things and am getting frustrated with having to constantly reinstall ubuntu which is understandable.

---

### Post by werries on 2008-07-31
What is your wireless card? (or at least post the output of the command:   lspci | grep "controller"


What have you tried to do?
What do you mean by, deleting the driver and reinstallating?

---

### Post by ozanamn on 2008-07-31
Hey Sorry for not being more specific

This is what i get from Lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
05:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:0a.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 

When I say I delete the driver i mean i actually have to remove the driver from ndiswrapper before i turn the computer off so that when the pc boots up next time the wireless doesn't load and prevent the computer loading. 

Thanks for you time, :D

Oz

---

