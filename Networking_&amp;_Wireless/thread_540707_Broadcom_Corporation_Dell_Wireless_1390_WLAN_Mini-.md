---
title: "Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by jmarcellais on 2007-09-01
I have a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) on my Compaq Presario notebook. I followed the steps given in 
[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)
 i got all the way to the end and rebooted, but I still cannot see my wireless adapter. Under network settings all I see is Wired connection and Modem connection. 

Also, when I enter *$ sudo iwlist scanning* into the terminal, i only get  
[I]
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.[/I]

Any ideas?

-Joe ¨The Linux n00b¨

---

### Post by scrooge_74 on 2007-09-01
It would seem your card is not been recognize by the system

---

### Post by jmarcellais on 2007-09-02
Ok, After i did a reinstall of Ubuntu, the card is now recognized, the wireless indicator light is also turned on now which was never the case previously. I can enable the wireless feature from the network icon next to the clock, and enter my home wireless information, but am still getting no connection.

also,*$ sudo iwlist scanning* now gives me...
[I]
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning : No such device[/I]

Do you think I need to go through installing the driver in steps from the link above?

*UPDATE*
Now after going through the steps in the link above, the wireless adapter is no longer recognized. I'm back to the previous iwlist scanning list and the wireless option is now gone from the network icon next to the clock. I was closer before I tried to install the driver. I'm gonna do another reinstall and take it from there.

---

### Post by jmarcellais on 2007-09-03
Ok, I followed the WifiDocs/WirelessTroubleShootingGuide and found something that is probably causing the problem, but as of yet have been unable to find a fix for it. here's what I got...

```
jmarcellais@joesLinux:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:73:28:79:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:50000000-50003fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth1
       version: 10
       serial: 00:16:d4:c1:d2:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.206 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:20

```

---

### Post by delibercogito on 2007-09-03
I've been trying for over 12 total hours to get a Broadcom Corporation Dell 1390 WLAN Mini PCI Card working.  I've tried every HowTo on the entire internet.  I even went so far as to make every different attempt on a completely fresh install to avoid leftover complications.  I am happy to say, that it now works. 

Now, WHY it works, makes little sense.  But it does.  This is on an Acer Aspire 5570-2052.  This is with a completely clean install from a Ubuntu 7.04 LiveCD.  Completely clean meaning I DID NOT DO ANY UPDATES.  I am sure that based on previous issues, UPDATES WILL BREAK THIS.

YOU MUST HAVE A USB WIRELESS ADAPTER FOR THIS TO WORK.

Skip the following UNLESS you are using an Acer that is listed as compatible here: [http://code.google.com/p/aceracpi/wiki/SupportedHardware](http://code.google.com/p/aceracpi/wiki/SupportedHardware) 

Go to:
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

Download acer_acpi-0.8.1.tar.bz2
Extract it.

Open a terminal and navigate to the acer_acpi-0.8.1 directory.
make
sudo make install

Follow this guide: [http://ubuntuforums.org/showthread.php?t=224349](http://ubuntuforums.org/showthread.php?t=224349) starting at Load the acer_acpi into memory and activate the wireless:

Note the typo in the original post at:


Code:

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

should be

Code:

ls /etc/rcS.d/S39acer_acpi_wireless_enable
ls /etc/rc0.d/S34acer_acpi_wireless_enable
ls /etc/rc6.d/S34acer_acpi_wireless_enable

Finish the guide and reboot.

Go to [http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/)

Download and install 	bcm43xx-firmware_1.3-1ubuntu2_all.deb

reboot.

You'll notice that network manager will still not list any networks.

Plug in a USB Wireless Adapter. I used a Linksys WUSB54GC.  Wait for a second.  Click on Network Manager again.  It should now list both wireless devices.  Unplug the USB adapter.  Your onboard wireless should still list networks at this point.  Make sure you can connect to one.  Reboot.

[I plugged in the Linksys adapter because I'd given up on getting the onboard to work and figured I'd just try the USB adapter.  Imagine my suprise (and cursing) when suddenly, the onboard worked.]

---

### Post by jmarcellais on 2007-09-03
> **delibercogito said:**
> 
YOU MUST HAVE A USB WIRELESS ADAPTER FOR THIS TO WORK.

Skip the following UNLESS you are using an Acer that is listed as compatible here: 

I have a Compaq laptop and I don't have a USB wireless adapter, so this doesn't really help me.

---

### Post by jmarcellais on 2007-09-03
ok, I found another thread that I followed and installed the bmc4xx driver installer, which I think was a mistake, especially since I don't have that model wireless adapter. Now I'm getting this...

```
jmarcellais@joesLinux:~$ sudo lshw -C network
Password:
  *-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:50000000-50003fff irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth1
       version: 10
       serial: 00:16:d4:c1:d2:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.206 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:20
```

I've already done two clean installs already and would like to avoid another.

---

### Post by jmarcellais on 2007-09-03
after yet another clean install I'm getting the following...

```
jmarcellais@joesLinux:~$ sudo lshw -C network
Password:
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:73:28:79:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:50000000-50003fff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth1
       version: 10
       serial: 00:16:d4:c1:d2:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.206 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:20

```

```
jmarcellais@joesLinux:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Ben Stewart on 2007-10-13
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I had exactly the same card and problem.

This method worked for me.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Ben

---

