---
title: "Atheros 5006EG Nightmare"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by Blind-Summit on 2007-11-10
Hi everyone,

I have spent the last 3 days trying to setup a dual boot of Ubuntu on my new Samsung R60. After fixing an issue with the display drivers not working (I am happy to share my fix), I am now trying to get my WiFi to work.

The laptop comes with the Atheros chipset (5006EG) and I have browsed for many solutions. Most of them seem to use this madwifi and ndiswrapper.

I had previously managed to use ndiswrapper with my desktop and a broadcom driver (Belkin wifi card) and this worked perfectly. I have managed to install ndiswrapper and load up the inf file that it supposedly needs. Whilst the driver is loaded and the hardware is detected (by ndiswrapper and the device list), it won't show up in the network manager.

Most of the forums that report the card working are using the Acer laptops and this won't work for me (I have tried as best I could)

Can someone please help me out here. I am copying commands from topics, and I don't really understand all of them.

Thanks in advance for your help

Alex

---

### Post by LANdiver on 2008-03-13
You are not alone. On my Acer Aspire it also doesn't want to work(((

---

### Post by kammpler on 2008-04-27
hi there, i use to have the same problem as you had, my solution was so simple, i have to look for the acer_acpi, 'cause every thing that you do works, the treat is that the wireless doesn't have the power supply, so you havee to install the acer_acpi, see this how to for more details.

[http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi)

---

### Post by beN..87 on 2008-05-30
> **Blind-Summit said:**
> Hi everyone,

I have spent the last 3 days trying to setup a dual boot of Ubuntu on my new Samsung R60. After fixing an issue with the display drivers not working (I am happy to share my fix), I am now trying to get my WiFi to work.

The laptop comes with the Atheros chipset (5006EG) and I have browsed for many solutions. Most of them seem to use this madwifi and ndiswrapper.

I had previously managed to use ndiswrapper with my desktop and a broadcom driver (Belkin wifi card) and this worked perfectly. I have managed to install ndiswrapper and load up the inf file that it supposedly needs. Whilst the driver is loaded and the hardware is detected (by ndiswrapper and the device list), it won't show up in the network manager.

Most of the forums that report the card working are using the Acer laptops and this won't work for me (I have tried as best I could)

Can someone please help me out here. I am copying commands from topics, and I don't really understand all of them.

Thanks in advance for your help

Alex

you need to use madwifi patch 3366 - nicedude has done a guide here (works perfectly on my samsung R60 plus )

link: [http://ubuntuforums.org/showthread.php?t=795984&highlight=samsung+r60](http://ubuntuforums.org/showthread.php?t=795984&highlight=samsung+r60) :guitar:

---

