---
title: "TP-LINK WN727N wireless adapter not working"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by brunolabs on 2014-05-25
Hello.

Can anyone help me with this problem?

Wireless script results:
```

########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux P5SD1-FM2 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8139]
	Kernel driver in use: sis190

##### lsusb #####

Bus 001 Device 007: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search lan

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

##### modinfo #####

##### modules #####

lp

##### blacklist #####

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

##### udev rules #####

# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

########## wireless info END ############
```


Thanks.

---

### Post by nknwn on 2014-05-25
Download the Windows driver from here: [http://uk.tp-link.com/products/details/?model=TL-WN727N#down](http://uk.tp-link.com/products/details/?model=TL-WN727N#down)
Make sure it unzipped. (I would create a folder named windowsdrivers in your home folder)
Plug in your device.
Install a program named ndisgtk using the software centre
When that has been installed open a terminal and type: sudo ndisgtk
In the Wireless network drivers window click install new driver
Another window lets you locate your newly downloaded driver
(you're looking for a filename ending in .inf)
Click install
Then configure your network from the Wireless Network Drivers window.

---

### Post by brunolabs on 2014-05-25
Hi!

Your instructions worked perfectly. The ndisgtk procedure accepted the windows driver.

However, I still can't connect or see the available wireless networks.

> **nknwn said:**
> Then configure your network from the Wireless Network Drivers window.

I tried to configure my own Wi-Fi network in the "Network Connections" menu but it doesn't show up when I click the "empty wifi icon".
Can you give me any tips on how to get the wifi connection working?


Thanks again for your help. :)

---

### Post by nknwn on 2014-05-25
I had trouble with such a driver recently. I'm still unsure what I did to get it working. I downloaded the addons for ndisgtk available in the software centre, but those amounted to source files. So it seems unlikely that those solved my problem. The only other thing I tried was simply a reboot.

---

### Post by brunolabs on 2014-05-25
Also downloaded those addons just to be sure. Still not working.
Thanks for your help with the ndiswrapper. ;)
With the driver installed it seems that I could be just missing some configuration now.

Does anyone have any ideas?

---

### Post by nknwn on 2014-05-25
Have you chosen the correct driver? There are 3 versions of the device I linked and in each zip file there are drivers for different versions of Windows. I chose the XP 32bit version.

---

### Post by brunolabs on 2014-05-25
I believe I did. I downloaded the v4 driver (checked from the usb adapter serial number) from the website and used for 'ndisgtk' the .inf in XP 32 bit folder.
I also tried the other ones (Win 7 and Win 8) but they didn't work. The driver from the XP 32 bit version was the only one that 'ndisgtk' accepted.

---

### Post by nknwn on 2014-05-25
Sounds correct. 
I was connecting a v3 the other day in Lubuntu. I installed ndisgtk and found there was a link available to it placed on the programs list. Lubuntu has a programs list that looks more like XP than Ubuntu. When I used that link I followed through the simple process of installing the driver but when it came to setting up the network I found that the window launched from the 'Configure Network' button just disappeared. It vanished. No message.

It turns out that in order to configure the network through that button successfully, ndisgtk had to be launched from the terminal with the escalated privileges of [B]sudo
[/B]I wonder if you are doing something that decreases your privileges in respect of setting up your connection ....

---

### Post by brunolabs on 2014-05-26
I also tried the instructions from here as it says it works for the WN727N as well:
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M]("https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M")
But without sucess. :(

Can anyone help me with this? Why is it so hard to configure a brand new adapter that is somewhat supported by Ubuntu? ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"))

What am I doing wrong?

I really welcome any hints to solve this problem.
Thank you.

---

### Post by kurt18947 on 2014-05-26
> **brunolabs said:**
> I also tried the instructions from here as it says it works for the WN727N as well:
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)
But without sucess. :(

Can anyone help me with this? Why is it so hard to configure a brand new adapter that is somewhat supported by Ubuntu? ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported))

What am I doing wrong?

I really welcome any hints to solve this problem.
Thank you.

Those rascals switched chipsets.  The RT5370 chipset used in v.3 has been plug & play for me, super easy.  V4 appears to be using a chipset I've never heard of:
[https://wikidevi.com/wiki/TP-LINK_TL-WN727N_v4](https://wikidevi.com/wiki/TP-LINK_TL-WN727N_v4)

**WI1 chip1:** **MediaTek** MT7601U

**Probable Linux driver**
[**[COLOR=brown]mt7601u_sta[/COLOR]**]("http://www.mediatek.com/en/downloads/")
**[USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**

That explains the difficulty.  This is a not uncommon occurrence with WiFi adapters and makes it a little risky to recommend wifi adapters.  A model which may be plug & play when purchased 6 months or a year ago may have switched chipsets without changing model numbers, like has happened here.  You typically can't determine the version number without opening the package and looking at the device's label.

---

