---
title: "Broadcom Chipset Help!"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by crazy dave on 2008-05-08
anyone know how to install firmware for Broadcom 4312 chipset on 64bit? I have tried advice on previous posts, ndiswrapper and fwcutter, but no luck.  Machine is HP Pavillion dv6522em(6500 series). Thanks in advance.

---

### Post by Ayuthia on 2008-05-08
You might want to check your lspci -nn (from the Terminal).  If you have a rev 02, the firmware on Hardy is currently not working well.  Most of those users have been using NDISwrapper.

Here is a link that you can try if it is not a rev 02:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

If you are not sure, feel free to post the results of your lspci -nn.

---

### Post by crazy dave on 2008-05-08
Thanks. Unfortunateley its rev02.....

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

I have installed the driver with ndiswrapper, which shows in the "Wireless Network Drivers" GUI as running with hardware present, however in Terminal, command ifconfig wlan0 returns, device not found.  I don't want to bin Ubuntu but I need Wireless.

---

### Post by Ayuthia on 2008-05-08
Can you post the results to the following:
```
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e bcm43xx -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e b43 -e bcm43xx -e ssb -e ndiswrapper
lspci -nn|grep 14e4:44
```
We need to make sure that bcm43xx and b43 drivers are blacklisted (the first command).  We also need to make sure that the proper modules are being loaded and sometimes ndiswrapper needs to be loaded at boot (command two checks this).  We also need to check and see if you need ssb for your wired connection (command three).  The b44 driver is the Broadcom wired driver and it needs ssb (a driver that needs to be loaded after ndiswrapper).

I am assuming that you have a wired connection.  If it is too much to post, I will try to help clarify what you need to have in each.

---

### Post by crazy dave on 2008-05-08
Thanks, results as follows.....

# replaced by b43 and ssb
blacklist bcm43xx

---

### Post by crazy dave on 2008-05-08
the second two commands returned nothing. I have a wired connnection as you say, and there appears tto be some sort of bridge ireless to the wired ifthat makes sense?

---

### Post by Ayuthia on 2008-05-08
Can you also check:
```
lsmod |grep ssb
```
If it only shows ssb and b43, you can do the next steps.

To see if ndiswrapper will work, try the following:
```
sudo modprobe -r b43 ssb
sudo modprobe ndiswrapper
```

If it works, you will need to add following:
```
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper |sudo tee -a /etc/modules
```
These commands will prevent the b43 module from loading (first command) and add ndiswrapper to /etc/modules so that it will load the next time you boot.

---

### Post by crazy dave on 2008-05-08
The first two commqnds return the following:

1. ssb                    37252  1 b44

2. FATAL: Module ssb is in use.

Perhaps I need a fresh install (again!)

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> The first two commqnds return the following:

1. ssb                    37252  1 b44

2. FATAL: Module ssb is in use.

Perhaps I need a fresh install (again!)
No! :) It is saying that your wired connection is a Broadcom.  It also means that my previous set of commands need to be modified.  Just to be sure that you do have a Broadcom wired card, can you post your lspci -nn information?

What we can do for now is test and see if your wireless works:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```

This will temporarily disconnect your wired connection, but should reconnect it again.  Worst case if you lose your connection is that you can reboot and nothing is lost.

---

### Post by crazy dave on 2008-05-08
The ethernet device is nvidia, here is th ehqrdware profile:


00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)


The three commands returned nothing, no apparent response?

---

### Post by crazy dave on 2008-05-08
The ethernet device is nvidia, here is th ehqrdware profile:


00:00.0 RAM memory [0500]: nVidia Corporation MCP65 Memory Controller [10de:0444] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP65 LPC Bridge [10de:0442] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation MCP65 SMBus [10de:0446] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP65 SMU [10de:0447] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0454] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP65 USB Controller [10de:0455] (rev a3)
00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
00:07.0 Audio device [0403]: nVidia Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP65 IDE [10de:0448] (rev a1)
00:0a.0 IDE interface [0101]: nVidia Corporation MCP65 SATA Controller [10de:045d] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:045b] (rev a1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:045a] (rev a1)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0458] (rev a1)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP65 PCI Express bridge [10de:0459] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
05:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)


The three commands returned nothing, no apparent response?

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> 
The three commands returned nothing, no apparent response?

That is a good thing.  Only error messages come up when doing this. What this means is that the modules unloaded happily and ndiswrapper loaded ok.  We can check that ndiswrapper is there by doing an lsmod|grep ndiswrapper.

Can you post the following:
```
lshw -C network
ifconfig
iwconfig
iwlist scan
```
It will see if the wireless is seen and working.

---

### Post by crazy dave on 2008-05-08
Thanks, returns as follows:

1.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:89:10:07
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.168 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb



2.

eth0      Link encap:Ethernet  HWaddr 00:1b:24:89:10:07  
          inet addr:192.168.1.168  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe89:1007/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3179188 (3.0 MB)  TX bytes:313293 (305.9 KB)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10248 (10.0 KB)  TX bytes:10248 (10.0 KB)

3.
lo        no wireless extensions.

eth0      no wireless extensions.

4.
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by Ayuthia on 2008-05-08
Ok.  Something is being stubborn.  Your lshw -C network is showing that the b43 module is still there.

Let's remove the b43, b44, and ssb module and then do check the device:
```
sudo modprobe -r b43 b44 ssb
lshw -C network
```
If all goes well here, that should produce an unclaimed card.  If that is true, try:
```
sudo modprobe ndiswrapper
lshw -C network
```That should produce a card using ndiswrapper.

---

### Post by crazy dave on 2008-05-08
> **Ayuthia said:**
> Ok.  Something is being stubborn.  Your lshw -C network is showing that the b43 module is still there.

Let's remove the b43, b44, and ssb module and then do check the device:
```
sudo modprobe -r b43 b44 ssb
lshw -C network
```
If all goes well here, that should produce an unclaimed card.  If that is true, try:
```
sudo modprobe ndiswrapper
lshw -C network
```That should produce a card using ndiswrapper.
removing b43 and b44 did produce an unclaimed card, as you said, however the command to use ndiswrapper didn't work, result as follows:

  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:89:10:07
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.168 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by Ayuthia on 2008-05-08
So now we know that the ndiswrapper module is not happy.  Let's try to figure out why.  To start, we will check and see if the version and driver are fine:
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by crazy dave on 2008-05-08
> **Ayuthia said:**
> So now we know that the ndiswrapper module is not happy.  Let's try to figure out why.  To start, we will check and see if the version and driver are fine:
```
ndiswrapper -v
ndiswrapper -l
```
OK; results as follows:
1.
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload

2. 
bcmwl6 : driver installed
	device (14E4:4312) present (alternate driver: ssb)

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> 
bcmwl6 : driver installed
	device (14E4:4312) present (alternate driver: ssb)
This is the offender!!  It is showing bcmwl6.  That is a Vista driver.  NDISwrapper is not ready for Vista drivers yet.  You will need to find an XP driver (bcmwl5).

---

### Post by crazy dave on 2008-05-08
> **Ayuthia said:**
> This is the offender!!  It is showing bcmwl6.  That is a Vista driver.  NDISwrapper is not ready for Vista drivers yet.  You will need to find an XP driver (bcmwl5).
Oops!  Have installed bcmwl5:

bcmwl5 : driver installed

However the GUI Ndiswrapper says "Hardware Present-No" bcmwl6 said yes

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> Oops!  Have installed bcmwl5:

bcmwl5 : driver installed

However the GUI Ndiswrapper says "Hardware Present-No" bcmwl6 said yes
From the terminal, can you post your ndiswrapper -l, and lshw -C network?

If they show bcmwl5 for the first and ndiswrapper + bcmwl5 (the bcmwl5 might not be there) for the second, try:
sudo modprobe -r b43, b44, ssb
sudo modprobe ndiswrapper
sudo iwlist scan

---

### Post by crazy dave on 2008-05-08
> **Ayuthia said:**
> From the terminal, can you post your ndiswrapper -l, and lshw -C network?

If they show bcmwl5 for the first and ndiswrapper + bcmwl5 (the bcmwl5 might not be there) for the second, try:
sudo modprobe -r b43, b44, ssb
sudo modprobe ndiswrapper
sudo iwlist scan
The first command returns:

bcmwl5 : driver installed

the second returns:

  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

sudo iwlist scan returns:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning

You've got the patience of a saint; I think I'll bury the laptop in the garden!

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> The first command returns:

bcmwl5 : driver installed[QUOTE]It should have shown something like this:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)

I am thinking that it does not like the driver.  Can you try another?

[QUOTE]You've got the patience of a saint; I think I'll bury the laptop in the garden!Why shouldn't I have the patience?  I am not the one with the problem!! :)

EDIT:  I am guessing that is why the Driver window gave that message.

---

### Post by stoneofshadow on 2008-05-08
i think i am having this same problem
i just upgraded to hardy and now i cant wirelessly connect to the internet
in the restricted drivers menu it shows that i should enable a "broadcom b43 driver" but it already says in use
and even if i click enable it does nothing
ive god the fwcutter packege but that did nothing
i havnt tried the other one yet
should i try what is above?

---

### Post by crazy dave on 2008-05-08
should't do any harm to try the above; but ask the expert, Im just a frustrated newcomer;

also try:

[http://us.ubuntu.cafuego.net/dists/hardy-cafuego/b43/](http://us.ubuntu.cafuego.net/dists/hardy-cafuego/b43/)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

[http://www.segundanariz.com/ubuntu/?p=31](http://www.segundanariz.com/ubuntu/?p=31)

[http://ubuntuforums.org/showthread.php?t=779754&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=779754&highlight=broadcom)

[http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+43xx](http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+43xx)

[http://ubuntuforums.org/showthread.php?t=652999](http://ubuntuforums.org/showthread.php?t=652999)

[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

You should go completely mad like me, after trying that lot!

---

### Post by Ayuthia on 2008-05-08
> **stoneofshadow said:**
> i think i am having this same problem
i just upgraded to hardy and now i cant wirelessly connect to the internet
in the restricted drivers menu it shows that i should enable a "broadcom b43 driver" but it already says in use
and even if i click enable it does nothing
ive god the fwcutter packege but that did nothing
i havnt tried the other one yet
should i try what is above?
Can you post your lspci -nn?  If your card is a 4312 rev 02 or a 4311 rev 02, you will need NDISwrapper.

---

### Post by crazy dave on 2008-05-08
> **stoneofshadow said:**
> i think i am having this same problem
i just upgraded to hardy and now i cant wirelessly connect to the internet
in the restricted drivers menu it shows that i should enable a "broadcom b43 driver" but it already says in use
and even if i click enable it does nothing
ive god the fwcutter packege but that did nothing
i havnt tried the other one yet
should i try what is above?
shouldn't do any harm, or if you want to lose your mind, try all of the following:

[http://us.ubuntu.cafuego.net/dists/hardy-cafuego/b43/](http://us.ubuntu.cafuego.net/dists/hardy-cafuego/b43/)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

[http://www.segundanariz.com/ubuntu/?p=31](http://www.segundanariz.com/ubuntu/?p=31)

[http://ubuntuforums.org/showthread.php?t=779754&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=779754&highlight=broadcom)

[http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+43xx](http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+43xx)

[http://ubuntuforums.org/showthread.php?t=652999](http://ubuntuforums.org/showthread.php?t=652999)

[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

---

### Post by Ayuthia on 2008-05-08
crazy dave-  Have you checked out this site?  You might try the driver from there.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

He has a 4312 rev 02 also.

---

### Post by crazy dave on 2008-05-08
> **Ayuthia said:**
> crazy dave-  Have you checked out this site?  You might try the driver from there.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

He has a 4312 rev 02 also.
thanks, tried it, have installed:
bcmwl5 : driver installed
bcmwl5a : driver installed

cqn't find any other drivers.

No Luck, do you think 32bit Hardy would be easier?

---

### Post by Ayuthia on 2008-05-08
> **crazy dave said:**
> thanks, tried it, have installed:
bcmwl5 : driver installed
bcmwl5a : driver installed

cqn't find any other drivers.

No Luck, do you think 32bit Hardy would be easier?
Not really. :(

I am thinking that you might try a Dell driver (I am looking for it).  Here is another one to try if you are up for it:
[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

EDIT:
One more:
[ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe](ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe)

By the way, how are you installing them?  Can you tell me the results of:
ls -l /etc/ndiswrapper

---

### Post by crazy dave on 2008-05-08
Thanks, driver found hardware in ndiswrapper, nothing showing on Wnetwork. thanks for your help, will try again tommorrow.

---

