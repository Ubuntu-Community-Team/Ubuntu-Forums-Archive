---
title: "NIC logical name changes every bootup"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by carlexpc on 2007-11-29
I have a new Acer Aspire 4520, and just like other owners of this brand and model, I am having a hard time setting up and making Ubuntu work seamlessly. 

Anyway, I have noticed that everytime I bootup, the logical name of the NIC changes, ex. eth0 to eth1, then when I bootup the next time eth1 turns to eth2 and so on. I am not even connecting any external NIC to my PC. I am looking for a valid explanation on this matter and at the same time a solution to fix the logical name to, say, eth0. Thanks!

*-network
          description: Ethernet interface
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0 
          logical name: eth6
          version: a2
          serial: 00:00:6c:5d:10:7a
          size: 100MB/s
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz

---

### Post by noob12 on 2007-11-30
What does 
```

 cat /etc/udev/rules.d/70-persistent-net.rules

```
say?

Are you seeing different mac addresses (HWAddr) from **ifconfig -a** each time you boot, or is the address stable? 

What driver is claiming the device?  Normally this would show up in the
```

sudo lshw -C network

```
output.   If it doesn't,  can you post the output of **lspci -nn**?

---

### Post by '888' on 2007-11-30
[http://ubuntuforums.org/showthread.php?p=3869356#post3869356](http://ubuntuforums.org/showthread.php?p=3869356#post3869356)

---

### Post by kevdog on 2007-11-30
Those instructions were thorough however the spelling and grammer were atrocious.  

> 
in default the first and second line aren't uncommented

A double negative??

So he means
in the default the first and second lines are commented??

---

### Post by '888' on 2007-12-02
hahaha....
yeah you're correct

i mean aren't commented

sorry there are some grammatical error:p
still learning...
thanx for ur correction

---

### Post by carlexpc on 2007-12-04
> **noob12 said:**
> What does 
```

 cat /etc/udev/rules.d/70-persistent-net.rules

```
say?

Are you seeing different mac addresses (HWAddr) from **ifconfig -a** each time you boot, or is the address stable? 

What driver is claiming the device?  Normally this would show up in the
```

sudo lshw -C network

```
output.   If it doesn't,  can you post the output of **lspci -nn**?

below is the result of  cat /etc/udev/rules.d/70-persistent-net.rules


```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:e0:4c:03:47:88", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:19:db:0c", NAME="eth1"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:f9:ff:6a", NAME="eth2"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:6e:cf:c0", NAME="eth3"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:4b:a1:97", NAME="eth4"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:f7:47:0f", NAME="eth5"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:5d:10:7a", NAME="eth6"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:c6:5e:bd", NAME="eth7"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:9b:65:4c", NAME="eth8"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:2f:ca:40", NAME="eth9"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:34:14:d8", NAME="eth10"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:76:fc:e6", NAME="eth11"

```

while below is the result of  sudo lshw -C network

```
 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth11
       version: a2
       serial: 00:00:6c:76:fc:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.50.29 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

---

### Post by oniichan on 2007-12-04
Strange. I have exactly the same problem with a Broadcom 4313 WLAN PCI card. On a previous install of 7.10 the wireless card worked flawlessly. For other reasons I did an absolutely clean install of 7.10 again. Following the same procedure with the same drivers it came up immediately. And now after every boot, it fails to load the driver for the wireless card (and so network:1 is UNCLAIMED). Re-installing the driver with ndiswrapper immediately restores wireless operation even with the prior network settings..
Also strange is the fact that the wireless card is 'off' after reboot.  Other threads attribute this to a windows problem which say this can be fixed by ensuring the wireless card is enabled and active before existing windows. Such is not the case here.
This is a dual boot with Windows XP and Ubuntu 7.10. I'm new to wireless on linux and am really stumped. I really don't want to do another clean install unless absolutely necessary. So I'm also going to try any ideas that shw up in this thread. Thanks.

---

### Post by limaxray on 2007-12-06
I have been having the same problem on my new HP laptop with an NVidia chipset and am currently up to eth101.  

I have tracked down the problem to be a bug with the NVidia forcedeth driver.  For some reason, it is reading the hardware MAC address backwards producing an illegal MAC address.  Linux detects this and fixes it by generating a random MAC address.  This in turn causes the NIC to be detected as a new NIC so the system gives it a new identifier.

If you do a 'dmsg' you can see what is happening.  Search through it and you'll find a line complaining "Invalid Mac address detected:" followed by your backwards MAC address.  This is followed by a line saying "Please complain to your hardware vendor. Switching to a random MAC."

I have not found a fix for it yet and I'm pretty sure NVidia hasn't fixed their drivers yet.  I still need to do more searching, but since their drivers are open source, I might just have to fix it myself if I can't find another solution.

---

### Post by limaxray on 2007-12-12
So I've done a little more research and this is what I've found:

It seems that certain motherboard manufactures on certain models have incorrectly implemented the functionality in the BIOS that returns the MAC address to the driver.  For some reason, it is returning it backwards from what is required in NVidia's standard.  So the consensus amongst the forcedeth developers is that this is a BIOS bug and not their problem.  They have even refused to allow others to submit a fix.  They simply suggest reporting the issue to the motherboard manufacturer and hope they make an update to the BIOS.  I personally disagree with this, seeing as the Windows drivers have no problem automatically correcting for this, I see no reason why the Linux drivers can't.  

I have sent an email to HP explaining the problem to them, but I really have no faith in their support.  There are some patches to forcedeth floating around that are supposed to fix this, but I have yet to get one to work correctly.

---

### Post by bogaczew on 2008-03-30
i use ubuntu 7.10, 64 bit athlon edition. i have the same problem with changing mac, following instructions from this forum i changed /etc/udev/ files and now i have only eth0 interface, but the mac address of this interface is still changing after every boot. i have local dhcp and dns server, my profile is assigned to my based on my mac address so it's very importent to me to have one, stable mac.i try to walk around this problem by setting manually desired mac address. i  wrote  a script, which changes mac adrress using macchanger, i put it in /etc/init.d and linked to /etc/rcS.d. as i assume network is started by /etc/networking, linked to /etc/rcS.d/S40networking. i linked my script as /etc/rcS.d/S39setMAC and it don't work. mac address is changed, but network doesn't start, after loging to gui (gnome) the system is frozen for few seconds, and eth0 does not have IP address.. it helps when i do```
 /etc/init.d/networking restart
```, i can put this in /etc/rc.local , and after this restart network starts fine, everything is working. but, why it doesn't work, when i simple change mac address during boot sequence?

---

