---
title: "Enable wireless on BCM4310 nic. How?"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by rootware on 2008-01-05
Hi everyone! I have a problem in setting up my WLAN network card. Has anyone idea how to enable it? Because after typing the lshw command, it seems to be disabled.

PS: My wireless router uses **WPA2** encryption mode, and I am using **Ubuntu 7.04**
Thanks a lot!

> *-network **DISABLED**
             description: Wireless interface
             product: **BCM4310 UART**
             vendor: **Broadcom Corporation**
             physical id: 0
             bus info: pci@03:00.0
             logical name: eth1
             version: 02
             serial: 00:00:00:1a:73:c3
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=0 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:b0200000-b0203fff irq:20


---------------

**_[COLOR="Red"]SOLVED![/COLOR]_**

So, here are the commands:

> [B]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo apt-get install ndiswrapper-utils-1.9

mkdir ~/bcm43xx; cd ~/bcm43xx

sudo apt-get install cabextract

wget [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)

cabextract sp34152.exe

ndiswrapper -i bcmwl5.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo cp /etc/network/interfaces /etc/network/interfaces.ori

echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

sudo ndiswrapper -m

echo 'ndiswrapper' | sudo tee -a /etc/modules

echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

reboot[/B]

full link here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

---

### Post by lgambett on 2008-01-05
Some broadcom cards need their firmware, that cannot be shipped with Ubuntu due to copyright reasons. Anyway you can easily install the firmware installing the package bcm43xx-fwcutter either via Adept Manager or sudo apt-get install bcm43xx-fwcutter.
Good luck !

---

### Post by rootware on 2008-01-05
> **lgambett said:**
> Some broadcom cards need their firmware, that cannot be shipped with Ubuntu due to copyright reasons. Anyway you can easily install the firmware installing the package bcm43xx-fwcutter either via Adept Manager or sudo apt-get install bcm43xx-fwcutter.
Good luck !

Nevermind, I figured out how to do it. You must fallow carefully all the steps in here:  

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

See the resuming commands on the first post.

---

