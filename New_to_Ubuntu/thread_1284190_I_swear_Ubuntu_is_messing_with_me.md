---
title: "I swear Ubuntu is messing with me"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by elsrkite on 2009-10-06
Randomly, as far as I can tell, Ubuntu has been switching themes when I log in. The menu bar looks a little different, some of the icons change. The appearance of the menus change, with the highlighting looking different. And in one of them, the keyboard volume controls don't work. I took screenshots of the two but I wasn't sure if I should just put them up here or somewhere else.

Oh, also occasionally it'll log me in on a really low resolution in the "standard" theme. And if I change the resolution, it gives me a window with the same number of pixels that takes up 1/3 of my screen. I have to log out and back in to fix it.

What is going on?

---

### Post by HarrisonNapper on 2009-10-06
Upload the screencaps as well as the output of lspci (in a terminal)

---

### Post by elsrkite on 2009-10-06
[IMG]file:///home/davidkeeling/Documents/Internet%2520help/Screenshot%2520Normal.png[/IMG]Here are the screen shots. What does lspci do?

---

### Post by HarrisonNapper on 2009-10-06
It lists all devices plugged in to a PCI bus on your computer. Among other things, it will tell us what kind of video card you have. If you want to create a file in your home directory for the output and attach that, simply do the following:
```
lspci > filename.txt
```
You can then attach filename.txt which will contain the information required. I find it easier just to copy and paste it into a code block in your post, though ;-)

---

### Post by HarrisonNapper on 2009-10-06
It actually looks like it might be something with gnome-panel. We'll take a look at the lspci, but can I get anyone else to ditto on the gnome-panel suspicion? Or maybe an applet on the panel?

---

### Post by achase79 on 2009-10-06
You can also check system->preferences->appearance and see if it set to randomly select a different theme for each login.

---

### Post by elsrkite on 2009-10-06
Yeah, fair enough. Here it is:

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

I feel so exposed.

---

### Post by elsrkite on 2009-10-06
> **achase79 said:**
> You can also check system->preferences->appearance and see if it set to randomly select a different theme for each login.

No, doesn't look like it. This was helpful though, I didn't even know where the themes were coming from. Had the computer for 3 months and I haven't even changed the desktop background.

---

### Post by HarrisonNapper on 2009-10-06
> **elsrkite said:**
> Yeah, fair enough. Here it is:

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

I feel so exposed.

Okay, for further troubleshooting, we need your myspace profile picture. Just kidding.

Not sure if this will work for an integrated graphics card, but have you tried System>Administration>Hardware Drivers? The only thing I can think is happening is a different video card is being detected each time or a different solution tried, making it wonky. Are you running a 32-bit or 64-bit install? Seems like people have had some problems on the 64-bit end with this.

---

### Post by HarrisonNapper on 2009-10-06
Also, make sure you've run your update (System>Administration>Update Manager).

---

