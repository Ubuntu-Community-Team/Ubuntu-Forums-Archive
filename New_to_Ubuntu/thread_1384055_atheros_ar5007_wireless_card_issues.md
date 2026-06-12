---
title: "atheros ar5007 wireless card issues"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by jhazard112 on 2010-01-17
i just loaded 9.10 karmic koala remix on my asus eee pc 900...i cant seem to load the drivers for my wireless atheros ar500 card... i have no idea what to do and i am kind of lost...i am a complete newb...any help is greatly apprecaited...

---

### Post by warfacegod on 2010-01-18
Go to System> Admin.> Hardware Drivers and activate the recommended wireless driver. If there is one, you might want to activate your video driver as well, while you are there.

---

### Post by jhazard112 on 2010-01-19
i tried that and it does not come up with any propreitary drivers...with that being said I found something for 8.04 but it did not work.  is there any other way to do it...i am completely lost on this one...i thought i had a good grasp of it but it doesnt work for me...let me know please...

---

### Post by warfacegod on 2010-01-19
Did the wireless work when you treid the LiveCd environment while installing?

---

### Post by lambengolmor on 2010-01-19
I'm not sure about this... Probably to make ubuntu see the restricted drivers you should have an internet connection, for example through ethernet... Anyway can you post lspci and lsusb output? That way we can know if the system is completely unaware of the wireless card or if the problem is somewhere else...

---

### Post by synapsys on 2010-01-19
The ar5007 chipset requires the ath5k driver which is included in Debian kernel images >=2.6.24

Please post the output of 

```
iwconfig
```

---

### Post by jhazard112 on 2010-01-22
I tried hooking my laptop to an ethernet connection and it has no issues getting to the internet.  Then I tried to repull the drivers in Hardware Drivers and no proprietary drivers came up again.  So I ran all that commands that you guys asked me to and I am posting them now...hope someone can help...Thanks in advance.

hazard@hazard:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



hazard@hazard:~$ lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

hazard@hazard:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

If you need me to run anything else or have any ideas I am all ears...again thank you in advance.

---

### Post by bkratz on 2010-01-22
> **jhazard112 said:**
> I tried hooking my laptop to an ethernet connection and it has no issues getting to the internet.  Then I tried to repull the drivers in Hardware Drivers and no proprietary drivers came up again.  So I ran all that commands that you guys asked me to and I am posting them now...hope someone can help...Thanks in advance.

If you need me to run anything else or have any ideas I am all ears...again thank you in advance.



Unless I'm blind..........
I don't see it listed in the lspci output at all. Could it be turned off in the bios, or maybe some external switch or key combination?

---

### Post by jhazard112 on 2010-01-22
Heres the weird thing...I dont see anything under Hardware Drivers when I run it...does that mean that they have already been installed, or that they are not being picked up?

---

### Post by lambengolmor on 2010-01-22
Ok, basically the system is unaware of your wireless hardware. So:

1) hardware broken (hope that's not it)
2) switch off (do you have some kind of switch on your pc to turn wireless on? If yes, how is it?)
3) wirless off by bios settings (you should enter your bios (esc, del, F-something just after you turn the pc on, it depends from pc to pc) and look for some entry about wireless)
3.1) if you have wirless on from bios but it still doesn't work you could need to update the bios (seen that once, not exactly a pretty situation). You can look on the net for how to do it for your pc, or ask again here if you have doubts.

Good luck

---

### Post by warfacegod on 2010-01-22
> **jhazard112 said:**
> Heres the weird thing...I dont see anything under Hardware Drivers when I run it...does that mean that they have already been installed, or that they are not being picked up?

These guys are correct, your wireless card is not showing up in the output. Hardware Drivers won't show a driver if your computer doesn't see the card. Instead of using lspci, look through the output of:

```
sudo lshw
```

If it's not a pci card, lshw should show it to you. Of course, I've never heard of a non-pci wireless card but anything's possible.

To add .04 to lambengolmor's list is the possibility that you don't have a wireless card?

---

### Post by jhazard112 on 2010-01-22
i am so mad right now...thank you guys it was disabled in the bios...i cant believe i didnt think of that...i mean i do this for a living working on computers, obviously with windows machines but still makes me mad that i didnt think of it...thanks to everyone for the posts and i hope i can help someone else as much as you guys have helped me...one last thing... are there any good books to read that can get me through ubuntu and understanding commands or unix/linux in general...any help would be awesome...

---

### Post by warfacegod on 2010-01-22
[http://ubuntuforums.org/showthread.php?t=1052065]("http://ubuntuforums.org/showthread.php?t=1052065")

Don't forget to mark as solved under thread tools.

---

