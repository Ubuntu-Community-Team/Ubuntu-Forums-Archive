---
title: "Slooooooooow Internet/network connection on laptop"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2007-05-13
My new HP laptop came with M$ vista preinstalled on it, which I used when downloading various versions of Linux.  Its wireless connection [to my Linksys WRT54G router] was blazingly fast.  So I install Ubuntu--first 7.04 and then, after two days of running around in circles trying to get the wireless connection to work (it was never even recognized), I gave up and put 6.10 on it--and now I'm connected to my network.  Great!  Except for one thing: My connection is SO SLOW it's like using a 1200 baud dialup modem in 1985! :shock: 

The Internet connection is terrible, but so is the connection to other computers on the network.  I frequently get timeouts when trying to access directories on the other computers (which are a mix of windoze and Linux boxes).

What can I do to bump up the connection speed?  I really don't have the patience to use anything that's this slow!  (And it pains me to point out that the same laptop, in the same spot in my house, booted up under 'doze has VERY fast connections to both my ISP and LAN...so it's not a problem with the router, my ISP, etc.)

---

### Post by Old *ix Geek on 2007-05-15
Anyone?!

---

### Post by earobinson on 2007-05-15
you could try using ndsiwrapper to install the windows drivers on your linux box., This sounds like a bug with your linux drivers.

could you post the output from lspci

---

### Post by Old *ix Geek on 2007-05-21
I've used ndiswrapper to install the Vista driver for my card, but it hasn't helped. I've even used an alternate, older version (XP) as suggested on the [ndiswrapper page](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33) at SourceForge, since Vista drivers are still not actually supported. No luck.  My connection is MISERABLY slow.  :eek:

I've done so much experimenting, tweaking, installing, uninstalling, etc., that at this point I don't even have a clear picture of where I stand (last night, in the midst of more attempts, I completely lost my wireless connection, but got it back), but here's the output from lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by Kobalt on 2007-05-21
You have a Broadcom 4311 : did you follow [these steps]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29") ?

---

### Post by Old *ix Geek on 2007-05-21
I had tried various other Broadcom-specific instructions, but not the ones you listed, Kobalt.  I'm off to give that a try!

---

### Post by Old *ix Geek on 2007-05-21
...and now I'm posting this from windoze because I've entirely lost my wireless connectivity on Ubuntu.  I followed those instructions to the letter and everything looked great (i.e., all results were as expected), until I rebooted (as instructed).  Now I can't connect to anything (network or Internet) and have no idea what's wrong.  :(  I think I'm CLOSE, though, because there are signs of life!  But I don't know what else to try...or check...or tweak.  If output from any commands or logs would be helpful to anyone, let me know and I'll post them!

---

### Post by Old *ix Geek on 2007-05-22
UPDATE: I'm connected...FAST!  That's the good news.  The bad news is that I literally have no idea how or why it started working.  Last night I was about to wipe the drive and do a fresh install because I thought I had screwed things up beyond hope.  Instead, I kept tweaking/modifying and deleting files by hand/re-doing the ndiswrapper steps, etc.  And just when I was about to throw in the towel for the night...I did SOMETHING and I suddenly had wireless again.  So I tried loading my pre-set group of tabs in SeaMonkey and they loaded like lightning. :p  With a happy look on my face I called it a night.

This morning when I fired up the laptop...no connection.  I tried to remember the last things I did last night so I could repeat them.  Without doing anything at a command line, I got it working again--I believe what did it was using "Wireless Assistant" to manually connect.  (I just realized that I had removed 'ndiswrapper' from /etc/modules at some point along the way.  I've reinserted that now and will see if that solves the problem at next reboot.)

---

