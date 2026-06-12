---
title: "i'm so very lost, and new"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by catholickid on 2007-08-08
so i just installed xubuntu on to my old dell inspiron 1000 laptop, i have an airlink mimo wireless card, and can't seem to connect to my open wireless network at home. i've tried everything i could understand in the forumns and help guides but i'm frankly lost, can someone please help me?

---

### Post by shavenlunatic on 2007-08-08
I can't help you with wireless(as I don't have any), but I can help you to get help.  Try including more info, error messages, what is actually happening, your network status etc... just saying it isn't working will only get the response "how isn't it working?"

Just trying to save you some time fella :)

---

### Post by catholickid on 2007-08-08
thank for the advice shaven, my network is an unencrypted wireless network by way of an airlink mimo router, at login i get an error stating that the system cannot find an ip address for figmant(computers name) and that this may cause xfce to not work properly. when i go into the settings-network section it does not give me an option to connect to unsecured wireless, only to put in a wep (hex or ascii) key, as far as i can tell i don't have a network manager and i can't view available wireless networks. but the compte does recognize that my wireless card is a network device andrecognizes it as a wireless card. so i'm still very lost a to what to do, but i was able to connect via ethernet at my office with no problems.

---

### Post by catholickid on 2007-08-08
exact wording of the error : Could not look up internet address for Figmant.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
Figmant to the file /etc/hosts on your system.

i have added Figmant to the hosts file.

---

### Post by kevdog on 2007-08-08
Lets start with some basics

Does you wireless card work??

If it does, did you install drivers for it??

Please type and the command line the folowing and cut and past the output:

lshw -C network
lspci -nn

---

### Post by catholickid on 2007-08-08
root@Figmant:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:c0:b2:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.34 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:e4003000-e4003fff irq:21
  *-network
       description: Wireless interface
       product: Ralink RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       logical name: ra0
       version: 00
       serial: 00:14:a5:33:3d:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:34000000-34007fff irq:16


root@Figmant:~# lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 650/M650 Host [1039:0650] (rev 80)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] [1039:0962] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]
02:00.0 Network controller [0280]: RaLink Ralink RT2600 802.11 MIMO [1814:0401]


the card worked before i installed the xubuntu..., i thought  it was already recognized.

---

### Post by willskills on 2007-08-08
If you use DHCP on the router - just try kicking it's butt from the terminal - my laptop's wireless card is the same chipset as yours - and network manager does not like it for some reason (I am not a fan of network manager)

sudo ifup ra0 

That should get you going :)

Edit - why are you logged in as root?

---

### Post by catholickid on 2007-08-08
ifup: interface ra0 already configured

<< >> (no IP address) still.

as far as the root thing the terminal said i should be doing the other command as  a super user.

---

### Post by kevdog on 2007-08-09
For a newbie you have your work cut out for you.  

I recommend upgrading the rt61 drivers to the cvs serial monkey rt61 drivers since the default drivers are very old and give many people headaches (such as yourself)

Here is a link to the serial monkey site:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

Now as far as how to actually install these drivers, I want you to look at this thread that explains how to install the rt73 drivers -- drivers that are the sister to your rt61 drivers.
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Read these instructions about 3 times before doing anything and use some common sense in the installation method.  Because the thread is intended for the rt73 drivers, you are going to have to substitute 61 where ever 73 is mentioned.  Again a little common sense about what you are trying to  accomplist will go a long way

Post back if you need help.

---

