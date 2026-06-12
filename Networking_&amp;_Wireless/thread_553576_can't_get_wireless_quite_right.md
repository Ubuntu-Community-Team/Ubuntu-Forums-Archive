---
title: "can't get wireless quite right"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by noob_ss on 2007-09-17
Hey everyone, id appreciate some help.. im new to this whole linux thing and i cant get it to work with my wireless. it doesn't seem to be recognizing my card.  I've done some online searching, followed tutorials to get ndiswrapper installed and everything seemed to go well.  i added my driver andd it gves me a message saying hardware is not present.  here is the output of my lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 01dd (rev a1)
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:09.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
03:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)


any help is greatly appreciated.

---

### Post by Junglizer on 2007-09-18
You're in luck! The MadWifi Drivers (Atheros chipset drivers) do indeed support that chipset. If you want you can save the file directly from the following link. Or aquire the file from [http://www.madwifi.org]("http://www.madwifi.org").
[http://superb-west.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.3.2.tar.gz]("http://superb-west.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.3.2.tar.gz")

Once you have the file downloaded you'll want to execute the following either using sudo or as root:
1) extract the archive
*tar xvf madwifi-0.9.3.2.tar.gz*
2) The previous command will make a folder named madwifi-0.9.3.2
change into this directory
*cd madwifi-0.9.3.2*
3) Then you'll want to compile
*make*
4) Step 3 will take a few minutes, depending on the speed of your processor. Now you need to install it, so the binary files will be in the proper locations.
*make install*

With that done you should then be able to delete both the folder and the .tar.gz file.

The main command that you use with the Madwifi drivers is *wlanconfig* the manual *man wlanconfig* should help you out, but here's roughly how you'd enter it:

*wlanconfig ath0 create wlandev wifi0 wlanmode sta*
Thats the command you'll more then likely use, wlanmode sta is the most common mode, basicly using it as a client card to connect to Access Points. The manual is very well written and understandable, I'm currently using these drivers for several different cards. Feel free to contact me if you have any problems.

---

### Post by noob_ss on 2007-09-18
when i ran the make command I got a bunch of compile warnings and errors.  seems to be referring to what should pretty standard c libraries.  stdio, etc.  just one example...

uudecode.c:26:19: error: stdio.h:No such file or directory

...ill post a full log of the output soon, but shouldn't this stuff be available out of box.  Am I missing some req'd libs or something?

---

### Post by kevdog on 2007-09-18
The reason you are getting those errors is that you dont have the build-essential package installed or linux headers:

Here is how to do this:


If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


One other suggestion for you -- but again would require a internet connection first.  Synaptic offers a precompiled version of the madwifi drivers.  The first thing to do is to figure out your kernel version:

uname -r
 
And then start Synaptic and do a search for linux-restricted.

If for example your kernel version is: 2.6.20-16-generic
Then you would install:
linux-restricted-modules-2.6.20-16-generic 

This will install the madwifi drivers (among with others for you).  Reboot.  
You might need to do a bit more configuring but at least it might save you a few steps.

---

### Post by Junglizer on 2007-09-18
Yeah, I don't actually *use* Ubuntu, so I wasn't sure if it was in the tree or not. Nor did I want to send them on a wild goose chase if it werent.

---

### Post by noob_ss on 2007-09-18
hmmm, ok.  I was able to run the make and isntall.  tried various flavors of the wlanconfig, but nothing seemed quite right.  I still doesn't seem to be able to recognize the card or something.  Under System -> Administration -> Network  I see 2 connections:
Wired Connection and Modem Connection.  shouldn't there also be a "Wireless Connection"?  I really appreciate the help, im eager to ditch windows and go with linux, but if i cant get my wireless network connection, unfortunately, my hands are tied.

---

### Post by kevdog on 2007-09-18
Please post the following

lshw -C network

This will tell us if your device is unclaimed by a driver, or if it is, what driver is associated with the device.

---

### Post by noob_ss on 2007-09-18
*-network UNCLAIMED
    description: Ethernet controller
   product: AR5006X 802.11abg NIC
   vendor Atheros Communication, Inc.
....


theres a bit more there, but id have to save to a log, transfer over to another machine,etc to post.  if you need all of it i will.  but the answer to your questions seems to be that it is "unclaimed"  what exaclty does that mean?

---

### Post by kevdog on 2007-09-18
Unclaimed means no driver is associated with your card.  Have you tried installing the linux-restricted module from synaptic yet??

---

### Post by noob_ss on 2007-09-18
no.  ill have to move the box to somewhere where i can access a wired connection.  ill try it tonight when i get off work.

---

### Post by Junglizer on 2007-09-18
When you've got some time post your *ifconfig -a* output. You should be able to get this up and working without all this random Ubuntu updating bullcrap, assuming you don't mind using the console.

---

