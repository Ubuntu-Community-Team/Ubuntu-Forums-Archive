---
title: "No WiFi after Lubu installation on Turbo-X Laptop"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by turbotoff on 2016-04-13
Hi Guys, 

I am new to the Linux world, though i have successfully installed Lubuntu on my girlfriend's old laptop which was sold under the brand Turbo-X / Model: X11A. I don't recall what version of Windows it was running before (Vista, i think), but i could not reinstall Windows after it got a virus, and decided to format the whole thing and install Lubuntu which appears to have gone through fine. I **can** get on the internet through ethernet and can do upgrades etc. My issue in the moment is Wireless. I can't see wireless networks at all. I suspect i need to override a setting in the BIOS setup (?). I tried one or two things already after reading some suggestions (cant remember exactly what), which have not worked. I am very proficient with Macs, I am semi-proficient with Windows, but I am completely noob with Linux.

Please can someone guide me on getting this working. Am hoping it's kinda simple to fix.

Please see attached photo of screen. When i hover over the wireless icon in the dock/lower menu bar, it has an exclamation mark and says: "wlp3s0 Connection has limited or no connectivity".

I think i am on v15.10

Also, it would nice if i could get the trackpad working, but that's secondary.
 
Thanks!

---

### Post by ajgreeny on 2016-04-13
On the laptop open a terminal and run the command ```
lspci
``` then paste back here the output from that using code tags.
See my signature below for a code-tags tutorial

---

### Post by howefield on 2016-04-13
And moved to the "*Networking & Wireless*" forum, probably a better fit.

A new thread can be opened for the secondary issue.

---

### Post by turbotoff on 2016-04-13
Ok, here's the output..

```
pinky@pinky-laptop:~$ lspci00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
pinky@pinky-laptop:~$ 
```

---

### Post by ajgreeny on 2016-04-13
There is no detected wifi adapter, only an Ethernet controller.

Are you certain there is one in the laptop, which if it had Vista must now be fairly old?

---

### Post by turbotoff on 2016-04-13
> **ajgreeny said:**
> There is no detected wifi adapter, only an Ethernet controller.

Are you certain there is one in the laptop, which if it had Vista must now be fairly old?

As i understand it, it could connect wirelessly before -- and i will double-check with the original user tomorrow, but i am fairly certain it could connect wirelessly. Is it possible something's gone amiss? Like the wireless functionality got shut off in some deeper settings of the computer. Or that the virus knocked it out? Or Linux is translating the adapter in a different way? Am just spitballing here. 

If we cant get around the adapter being detected, can i at least connect with a usb internet dongle?? If so, would this be a straightforward solution?? 

Thanks for your time and knowledge!

---

### Post by ajgreeny on 2016-04-13
I think the adapter would still be detected in all those circumstances.  Your list shows nothing.

A USB adapter is certainly possible; you just need to get one that is known to work with Linux, and that can be slightly more difficult, as makers have a habit of changing the chipset but keeping the same name for the adapter.

---

### Post by turbotoff on 2016-04-13
Ok, thanks. I think we are making some headway.

I found this dongle on eBay which i conclude may work, and am currently bidding for.. 

(*see uploads)

---

### Post by ajgreeny on 2016-04-14
Good luck!

The info suggests that the adapter has drivers for Linux, so I hope that is correct.

Keep in touch and let us know the outcome.

---

