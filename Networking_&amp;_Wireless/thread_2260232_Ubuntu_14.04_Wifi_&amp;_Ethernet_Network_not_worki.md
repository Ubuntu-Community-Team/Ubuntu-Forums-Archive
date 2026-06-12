---
title: "Ubuntu 14.04 Wifi &amp; Ethernet Network not working - Network Unclaimed"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by Nanogravity on 2015-01-10
Hi,

I am experiencing a similar problem. I followed the instructions that you mentioned in the previous reply and have generated the text file. Can you suggest me what needs to be done?

[PHP]
*************** info trace ***************
***** uname -a *****
Linux Lenovo-G470 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
***** lsb_release *****
Distributor ID:    UbuntuDescription:    Ubuntu 14.04.1 LTSRelease:    14.04Codename:    trusty
***** lspci *****
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)    Subsystem: Lenovo Device [17aa:3979]02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)    Subsystem: Lenovo Device [17aa:30a1]
***** lsusb *****
Bus 002 Device 004: ID 064e:a222 Suyin Corp. Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB StickBus 002 Device 005: ID 0951:1623 Kingston Technology Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 DeviceBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
***** PCMCIA Card Info *****

***** iwconfig *****

***** rfkill *****

***** lsmod *****

***** nm-tool *****
NetworkManager Tool
State: disconnected

***** NetworkManager.state *****[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=trueWimaxEnabled=true
***** NetworkManager.conf *****
[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq
[ifupdown]managed=false
***** interfaces *****
# interfaces(5) file used by ifup(8) and ifdown(8)auto loiface lo inet loopback
***** iwlist *****

***** resolv.conf *****

***** blacklist *****
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci
[/etc/modprobe.d/blacklist.conf]blacklist evbugblacklist usbmouseblacklist usbkbdblacklist eepro100blacklist de4x5blacklist eth1394blacklist snd_intel8x0mblacklist snd_aw2blacklist i2c_i801blacklist prism54blacklist bcm43xxblacklist garmin_gpsblacklist asus_acpiblacklist snd_pcspblacklist pcspkrblacklist amd76x_edacblacklist xpadblacklist xpadblacklist xpad
[/etc/modprobe.d/fbdev-blacklist.conf]blacklist arkfbblacklist aty128fbblacklist atyfbblacklist radeonfbblacklist cirrusfbblacklist cyber2000fbblacklist gx1fbblacklist gxfbblacklist kyrofbblacklist matroxfb_baseblacklist mb862xxfbblacklist neofbblacklist nvidiafbblacklist pm2fbblacklist pm3fbblacklist s3fbblacklist savagefbblacklist sisfbblacklist tdfxfbblacklist tridentfbblacklist viafbblacklist vt8623fb
***** modinfo *****

***** udev rules *****
# PCI device 0x1969:0x2062 (atl1c)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
***** dmesg *****

****************** done ******************
[/PHP]

Wireless.info.txt:

```

*************** info trace ***************

***** uname -a *****

Linux Lenovo-G470 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

***** lspci *****

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Lenovo Device [17aa:3979]
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lenovo Device [17aa:30a1]

***** lsusb *****

Bus 002 Device 004: ID 064e:a222 Suyin Corp. 
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 005: ID 0951:1623 Kingston Technology 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: disconnected


***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist xpad
blacklist xpad
blacklist xpad

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

***** modinfo *****


***** udev rules *****

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****


****************** done ******************

```


Thank you in advance.

---

### Post by praseodym on 2015-01-10
Yes, load the drivers:
```

sudo modprobe -v ath9k
sudo modprobe -v alx
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by coffeecat on 2015-01-10
@Nanogravity, I have split your post and praseodym's reply into their own thread, and given it a relevant title. The thread you posted to concerned a different wireless network adapter and different version of Ubuntu.

---

### Post by Nanogravity on 2015-01-10
Hi,

My Lenovo G470 has a dual boot Windows 7 and Ubuntu 14.04. Today My Ubuntu's Internet suddenly stopped connecting. I have tried various solutions presented on the web, but am unable to solve the problem. Can you present me with a solution? 

Problem: Network Unclaimed.

       [PHP]*-network UNCLAIMED    
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d0500000-d053ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d040ffff
[/PHP]


Thank you in advance.

---

### Post by coffeecat on 2015-01-10
Threads merged. I have renamed the merged thread (again) with your title

---

### Post by Nanogravity on 2015-01-10
Hi, Thanks for the reply.

When I run the "sudo modprobe -v ath9k" command, I get an error:[HTML] modprobe: FATAL: Module ath9k not found.[/HTML]

PS: I do not have internet on my Laptop. I can connect to internet if I boot windows or when I use a USB booted Ubuntu.

---

### Post by Nanogravity on 2015-01-10
> **coffeecat said:**
> Threads merged. I have renamed the merged thread (again) with your title

Thank you admin :)

---

### Post by praseodym on 2015-01-10
Ok, you need this file:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb)

Save it in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and run
```

sudo apt-get install --reinstall linux-generic
```

---

### Post by Nanogravity on 2015-01-10
> **praseodym said:**
> Ok, you need this file:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-43-generic_3.13.0-43.72_amd64.deb)

Save it in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and run
```

sudo apt-get install --reinstall linux-generic
```

Thank you Praseodym. **Problem solved**. I can connect to Internet now ! :) :D

---

### Post by PhotoMEX on 2015-10-27
Awesome, thanks Pr. All my problems have been solved now.

Out of the blue my login had switched from German keyboard to American (Kubunbtu 14.04 on Lenovo ThinkPad Edge Type 0196). It took me a while to figure that out; my password contains a couple of special characters. Also the wireless connection had stopped working (Ethernet was fine though). I was only trying to correct the wireless problem using Pr's fix, but now the keyboard is okay, too. When I ran

sudo apt-get install --reinstall linux-generic

I received an error message about dependencies (don't remember what it said exactly), but in the message it was also recommended to run 

sudo apt-get install

without further arguments, which I did. After rebooting everything - including the keyboard nuisance - was fixed.

Pr great, thanks again.

---

