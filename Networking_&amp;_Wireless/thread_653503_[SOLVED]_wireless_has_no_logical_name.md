---
title: "[SOLVED] wireless has no logical name"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by DrIdiot on 2007-12-30
I am using the intel  pro/wireless 3945abg network card in my laptop.  it was working fine until just now, where it, after my computer crashed and i had to do a hard reset, it stopped working.  after typing in

sudo lshw -C network

i get


harrison@abelian:~$ sudo lshw -C network
[sudo] password for harrison:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:bd:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.2.88 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

it seems that it did load the driver (ipw3945) but it has not been assigned a logical name.  also, it cant determine the mac address.  i am using gutsy.

does anyone know why this happened?

---

### Post by DrIdiot on 2007-12-30
*deleted*

---

### Post by DrIdiot on 2007-12-30
okay im connected by ethernet now so i can post more detailed information:


harrison@abelian:~$ sudo lshw -C network
[sudo] password for harrison:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:bd:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.2.88 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

### Post by DrIdiot on 2007-12-30
oh and i am using gutsy

---

### Post by DrIdiot on 2007-12-30
bump

---

### Post by willie_wang on 2007-12-30
I don't know if this will help, but check that the driver is still installed. your wireless won't receive a logical name until you have a driver installed.

you might need to use ndiswrapper [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

or just reinstall it using the method you had before for getting your wireless to run in the first place.

once the driver has been successfully installed, the logical assigned names are held under, /etc/udev/rules.d/70-persistent-net.rules.

```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

 if you can figure out the mac/physical address of your card, then you can check whether it is assigned a logical name or not here. if not, then manually add the details below:

SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0e:9b:cc:c5:05", NAME="wlan0"

replacing the mac address, 00:0e:9b:cc:c5:05, with your own.

---

### Post by DrIdiot on 2007-12-30
i did a modprobe of the driver, and it returned without error, so i assume they are successfully installed?

harrison@abelian:/etc/udev/rules.d$ cat 70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x1713 (tg3)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:a0:fc:bd:fb", NAME="eth0"

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:77:71:6c:6e", NAME="eth1"


it seems that they are given logical names as well?

---

### Post by DrIdiot on 2007-12-30
here are the results from lsmod:

harrison@abelian:/etc/udev/rules.d$ lsmod | grep iwl
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211

---

### Post by willie_wang on 2007-12-30
hmm... have you tried making sure your restricted modules are enabled? i've done a bit of reading and your card should work out of the box.

---

### Post by DrIdiot on 2007-12-30
well it did work... here's the backgrond info i posted somewhere else:

(im posting the entire email so theres some repeated information)

Background info: this laptop is a dell insipron 1420n that came prepackaged with ubuntu feisty.  i upgraded to gutsy.  the wireless card is an intel pro/wireless 3945.  i am currently using the iwl3945 driver.  every 21 reboots, linux wants to check the hard driver for errors.  however, conveniently, one time, it wanted to do this on an airplane that was about to take off.  i pressed ctrl+alt+del to shut the computer down.  after i got home, i could boot but i could no longer find my wireless card.  however, it does show up:

harrison@abelian:~$ sudo lshw -C network
[sudo] password for harrison:
 *-network                    description: Network controller
      product: PRO/Wireless 3945ABG Network Connection
      vendor: Intel Corporation
      physical id: 0
      bus info: pci@0000:0c:00.0
      version: 02
      width: 32 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list
      configuration: driver=iwl3945 latency=0 module=iwl3945
 *-network
      description: Ethernet interface
      product: NetLink BCM5906M Fast Ethernet PCI Express
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:09:00.0
      logical name: eth0
      version: 02
      serial: 00:1a:a0:fc:bd:fb
      size: 100MB/s
      capacity: 100MB/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.2.88 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s



it does not have a logical name or a serial (mac address?).  i have tried the ipw3945 driver, it doesnt help.  does anyone know why this isnt working and how i can fix it?

thanks.

-harrison

ps i posted abotu it here: [http://ubuntuforums.org/showthread.php?p=4039055#post4039055](http://ubuntuforums.org/showthread.php?p=4039055#post4039055)

---

### Post by willie_wang on 2007-12-30
also found this, which might help :)

[http://ubuntuforums.org/showthread.php?t=582606](http://ubuntuforums.org/showthread.php?t=582606)

---

### Post by DrIdiot on 2007-12-30
hmm... i tried those, but they dont seem to work for me.  it seems like they have a different problem.  for me, the wireless card is detected, the driver is working and "in use", and it's somehow recognized as a networking device (as seen in lshw-C network), but it isn't assigned a logical name?

---

### Post by DrIdiot on 2007-12-30
i think i have the same problem as in this post:
[http://ubuntuforums.org/showthread.php?p=4042193#post4042193](http://ubuntuforums.org/showthread.php?p=4042193#post4042193)

---

### Post by DrIdiot on 2007-12-30
i fixed it.  there was a stupid little switch on my laptop that turns the wireless off... thanks!

---

### Post by sujie on 2008-03-04
> **DrIdiot said:**
> i fixed it.  there was a stupid little switch on my laptop that turns the wireless off... thanks!


I am facing the same problem: no logical name for my 3945 adapter. I have turned the WiFi switch on, but the problem is still there. I installed xp and ubuntu 7.10 server edition in my Dell Inspiron 1420, and the wireless works well under Xp. Do you have any suggestions to the problem?  Thanks a lot!

$ sudo lshw -C network
[sudo] password for harrison:
*-network 
description: Network controller
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ipw3945 latency=0 module=ipw3945



Mar 7, 2008. 
I havd fixed the problem by reinstalling the ubuntu 7.10. The new ubuntu recognized both network cards.

---

