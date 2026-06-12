---
title: "Uh oh!  Wireless card doesn&quot;t work now"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-20
So I just wiped my hard drive and reinstalled win7 then Ubuntu.  My wireless card was working for both and now has stopped working in both.  I hit F2( i have a dell inspirion 1545 with a broadcomm wireless made dell 1397 mini card btw) to turn on the wireless numerous times but it doesn't do anything.  when I try and troubleshoot it it says to turn on the wireless card.  Maybe I should mention that I was at home when it was working and took my pc to my GF's   and when I tried to log on to her router(which I've done before as it's my router) it can't find any connection. I tried to download the drivers through system>admin>hardware drivers but it either wouldn't do it or my Ubuntu kept freezing up.  Is my wi-fi card burned out? I've only had this pc about 6 months.  Also I was using wubi and everything worked fine except for the lack of memory so that's why I installed the 10.04 LTS dual booted with win7. And one last thing is that my top bar is showing things twice(see pic, top right corner)  should I reinstall Ubuntu?

Thanks

Kevin
P.S.  it keeps saying I'm connected to my home network even though I'm no where near it, yet won't find any other wireless.

---

### Post by zkriesse on 2010-06-20
Hmmm...wireless...what happens when you run the following command in your Terminal. (The terminal can be found by going to Applications -> Accessories -> Terminal)

The command is
```

lspci

```

---

### Post by Kirkland14 on 2010-06-20
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```so it seems like its there.  I also found it in win as well.  hmmm

---

### Post by zkriesse on 2010-06-20
Ok... One thing that I tried was doing the "Try LiveCD" option instead of doing an install right away. What happened is after say, 10 minutes it said that it needed to install a proprietary driver for my wireless for it to function properly. I'd recommend that you try that and see what happens. If it doesn't work then we'll start trying other things.

---

### Post by diablo75 on 2010-06-20
If you haven't done it already I would highly recommend you find an ethernet cable to connect your laptop to your router/modem and use that to download all the latest system updates for Ubuntu using the Update Manager in the System menu.  After everything is applied try the hardware drivers manager again to see if you can enable your wireless drivers.  In a worse case scenario you'd probably be able to get the thing working using ndiswrapper.

---

### Post by Kirkland14 on 2010-06-20
> **diablo75 said:**
> If you haven't done it already I would highly recommend you find an ethernet cable to connect your laptop to your router/modem and use that to download all the latest system updates for Ubuntu using the Update Manager in the System menu.  After everything is applied try the hardware drivers manager again to see if you can enable your wireless drivers.  In a worse case scenario you'd probably be able to get the thing working using ndiswrapper.

i tried that because that's what I did when I was using wubi.  the thing is even win7 doesn't find wireless either so it doesn't just seem to be linux

---

### Post by diablo75 on 2010-06-20
Check your BIOS to see if there are ANY settings relevant to the wireless adapter.  I once had a laptop that gave control of enabling/disabling the wireless adapter to the OS.  Fortunately there was also an option to tell it to enable the wireless adapter right away and to not give control to the OS.  Switching this setting seemingly made the wireless card "appear" and I was able to connect to wireless networks after that.

It might also be the switch/button on the computer (if you have one) that is meant for turning wi-fi on/off.  Sometimes they don't really give you much indication of being pressed, but you might try booting, pressing it ONCE and then wait about 60 seconds to see if anything changes in the nm-applet in your upper panel.

---

### Post by Kirkland14 on 2010-06-20
i tried the switch but it's not working.  How do I check it in the BIOS?

> so now I'm back home and the wireless works for win7 but not ubuntu.  WTF?

---

