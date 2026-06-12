---
title: "no clue ho to make wifi it work"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Dracar on 2007-02-24
my pc is a dell inspiron b130, and for some reason it will not connect using a cable, i have to use wireless. it came with an internal wireless card that i have been using with its windows installation, but now i want to switch to linux. i have no idea how i couldn't even get the cable connection working if it wud work, im not good with netwroking stuff. can someone explain how to connect to an existing wifi network? is thre anything liek in windows? i jsut open a window and it has a list of possible networks, then i click connect?

---

### Post by gradedcheese on 2007-02-24
Assuming you're using normal Ubuntu with Gnome, go to System->Administration->Networking.  Do you see the card there?  If so, enable it, configure (and there you can select the network to join, etc).  If not, then post here and we can help but we'll need you to identify the hardware first.

---

### Post by Dracar on 2007-02-24
i was running the live cd, and yes it showed up in there, i enabled it, but i could not figure out what to do next, in my vm, when i run the installed ubuntu it doesnt show up, but in it i just share connection with windows...let me go get the livecd again, i will be back in 10 minutes i guess, im gunna c what it sais in configure, oh and i think i have ubuntu 6.06 or 6.6 sumthin like that, and i think it has gnome, i was testing vms and my freind sent me the dl link, i like it so im trying to switch to it...

---

### Post by gradedcheese on 2007-02-24
a VM isn't a good indicator: the VM provides a fake network interface (Ethernet card) to the guest OS, no matter what the real interface (Ethernet, WiFi, etc) is.  So the way it behaves in a VM has nothing to do with how it will work on real hardware.  The best way to tell is indeed the live CD (though some cards can work with a little bit of effort, but they won't work in the live CD).  The more surefire way, though, is to just look up exactly what chipset your LAN and WiFI cards use, then we can see how they'd be supported in Linux.

---

### Post by Dracar on 2007-02-24
um ok... well i looked on the live cd, and i noticed that yes, the wireless was showing up in networks, and it was set to default but, it was not acctive, so i activated it, that took 5 minutes, then i clicked ok, it took 5 minutes again b4 it shut the window, then when reopend, it said it was off again, and my indicator led was off the entire time. and hwen i lcicked properties, the dropdown for essid was blank, thats all that i noticed...

i am going to bed, i will check this post tomorow, please help and ty if you do, oh and idk if it will help, i downloaded kwifi manager.

---

### Post by gradedcheese on 2007-02-25
It will probably work then.  If you want to tell me what chipset you have, please do the following from Ubuntu: open the terminal via Applications->Accessories->Terminal and type "lspci" and then press Enter.  Post the output here.

---

### Post by Dracar on 2007-02-25
Ok, this is what i got..

```

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ubuntu@ubuntu:~$

```

---

### Post by gradedcheese on 2007-02-25
> 
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Ah, Broadcom :(  There are several 4318-specific HOWTO posts in this forum, (and in the tutorials forum I think), so you'll need to follow one of those.  The Ethernet card should at least be supported by the b44 driver, so that will work.

---

### Post by Dracar on 2007-02-25
ok, so it will work then? i didn't know it had like a brand or watever, i thought it was one of dells offbrand things. ok so search for broadcom or watever?

---

### Post by gradedcheese on 2007-02-25
You have a Broadcom BCM4318, that's what you need to search for (it will work via ndiswrapper but not otherwise, Broadcom is terrible for Linux support).  Dell has nothing to do with it, they bought the chipset from broadcom and slapped it on the motherboard.  You can [read more]("http://andrey.thedotcommune.com/wireless.html") about WiFi chipsets if you are curious about that goes in to one of these chipsets and why some work well while others need ndiswrapper.

oh, and here: have fun
[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

---

### Post by Dracar on 2007-02-25
yea, never hurts to learn. i tried a tut and it removed my wifi card from the networks thing... i just installed linux cause my windows ficked up. just got windows working again, i realy wanna remove it completly but i need to get linux internet working first. im gunna try again but i think it may get messed up...

i checked forumz, i found one but it said "These instructions do not apply to Ubuntu for Power PC (PPC) and the Ubuntu Desktop CDs. "
this is the file i used to install my ubuntu

ubuntu-6.06.1-desktop-i386.iso, i used nero to burn it to disk as a premade image, then installed it on my old backupdrive.

---

