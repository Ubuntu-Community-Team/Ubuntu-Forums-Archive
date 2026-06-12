---
title: "Trouble loading Ubuntu"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by GumpTron on 2009-04-26
i keep getting "your screen, graphics card, and input devices could not be detected correctly". I get this 9 out of 10 times I try to load Ubuntu and I don't understand whats going on.

if i try to boot Ubuntu i get this 9 out of ten times. Basically, when i try to load Ubuntu I am never sure it will!

Sometimes it loads but the graphics are all messed up. The screen is off center and its not good.

i basically never know if ubuntu will load properly.

HELP!

---

### Post by Sidewinder1 on 2009-04-26
What type of computer, graphics card, monitor are you using?
If you run the following command in Terminal and then copy and paste the results back here, I'm sure that we can help solve your problems...
```
lspci
```

---

### Post by GumpTron on 2009-04-26
> **Sidewinder1 said:**
> What type of computer, graphics card, monitor are you using?
If you run the following command in Terminal and then copy and paste the results back here, I'm sure that we can help solve your problems...
```
lspci
```

thanks for getting involved. let me try to boot ubuntu and see if i can get that for you. FYI i am using vista now as part of my duel boot.

---

### Post by GumpTron on 2009-04-26
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
0e:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
1a:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
1a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
1a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
1a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

ubuntu loaded and the graphics was an issue, the screen was cut in half. i tried restarting and now it loaded normally graphics wise. But like i said, 9 out of ten times it wont load the graphics correctly.

---

### Post by Sidewinder1 on 2009-04-26
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
That's the model of your graphics card. If you've already tried the proprietary driver...System--->Administration--->Hardware Drivers, (as I had to do with my NVIDIA), I don't know what else to suggest. The fact that sometimes it loads and sometimes it doesn't is a "real head-scratcher". Rather than tell you the wrong thing...Perhaps some more knowledgeable Guru will be able to help. Good luck,
Side

---

### Post by GumpTron on 2009-04-26
> **Sidewinder1 said:**
> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
That's the model of your graphics card. If you've already tried the proprietary driver...System--->Administration--->Hardware Drivers, (as I had to do with my NVIDIA), I don't know what else to suggest. The fact that sometimes it loads and sometimes it doesn't is a "real head-scratcher". Rather than tell you the wrong thing...Perhaps some more knowledgeable Guru will be able to help. Good luck,

Side

ill check that out and thank you for the advice.

---

### Post by GumpTron on 2009-04-26
FYI, Ubuntu always loads, i get the logo with the loading line, but 9 out of 10 times it will have graphics trouble and try reloading in various ways. It will then give me 4 choices to choose from to handle the problem. I usually choose to "load with low graphics (this time only)". it usually loads after that, but the graphics are messed up "the far top of the screen has bad graphics issues while the part of the OS that did load is kinda split in half. Kinda like if i were running duel screens, but on one screen!!

---

### Post by YourNeighbourNinja on 2009-04-26
Hi,
I have a problem with loading Ubuntu but of different kind. My friend installed Ubuntu for me and created a bootup list for me to choose an OS. I decided to delete the Windows and use only Ubuntu on this computer. Now, problem is that someone tried to load Windows from the bootup list and now it keeps booting it up without the list at the beginning. How can I get the bootup list back on so that I choose Ubuntu again? Please help me.

I hope I haven't intruded on the topic with this post.

---

### Post by Sidewinder1 on 2009-04-26
Welcome YourNeighbourNinja!
No' you're not intruding at all. However you will receive many more responses if you start a new thread. Since it sounds like someone installed (not booted; that should have no affect on menu.lst) windoze **after** Ubuntu, entitle your new thread "Restoring GRUB after windows install". There are plenty of folks, more than willing to walk you through the solution. 
GumpTron: The more that you write, it sounds more and more like a proprietary driver issue. Perhaps this thread will point you in the correct direction;

[http://ubuntuforums.org/showthread.php?t=1138223](http://ubuntuforums.org/showthread.php?t=1138223)

Or this:
[http://ubuntuforums.org/showthread.php?t=1135877](http://ubuntuforums.org/showthread.php?t=1135877)

Side

---

