---
title: "Atheros 5007EG Ubuntu 7.10 (Aspire 5104)"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by David26 on 2008-04-17
Hello, I am trying to install my Atheros 5007EG, in the past when I just got my laptop, I already noticed this annoying problem with other linux distributions (openSuse,Fedora etc). Anyway I thought we are a half year further now, I might consider installing linux again, after trying openSuse I discovered not much has changed on version 10.3. I thought I found the solution, but it was a bummer that I did not. Then I decided to use Ubuntu again like I did in the past. I installed Compiz-Fusion on it and some other applications, however I am still having problem with my Atheros 5007EG card. Someone said Atheros 5007EG is supported by Ubuntu 7.10. But it prob. is not, I do see a atheros driver in the restricted driver thingy. But I can't see any wireless network, can't connect to one. So now I am stuck to wired connection. And I hate to be wired.

Any help is appreciated,
Kind regards,
David90

---

### Post by chili555 on 2008-04-17
NetworkManager, which is installed by default, will not allow a wireless connection if wired is available. Please disconnect the wire and do:```
sudo ifconfig eth0 down
sudo iwconfig
```Did your wireless interface appear? ath0, perhaps? Do you see wireless networks now?

Post back and we'll help if you get stuck.

---

### Post by mavi_yelkenler on 2008-04-17
hi David. I have the same card and i am able to use it with the readily-patched snapshot on this page ==> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

but you sould also blacklist ath5k module and then restart and " sudo modprobe ath_pci "

mavi_yelkenler

---

### Post by David26 on 2008-04-18
still not working. I only see:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by growler on 2008-04-18
D26,
I'm using 8.04b (32 bit).....not long till the release date... Woo Hoo

Look here
[ http://ubuntuforums.org/showthread.php?t=742044]("http://ubuntuforums.org/showthread.php?t=742044")

growler.

---

### Post by David26 on 2008-04-18
Anyway i am facing another problem i installed WICD, anyway I am getting an error and cannot restart using the normal gnome network manager.

---

### Post by chili555 on 2008-04-18
For now, let's concentrate our efforts on the Atheros. Please let us see the results of:```
sudo modprobe ath_pci
```This should return nothing, meaning the module was inserted with no error. Then:```
sudo lshw -C network
```Thanks.

---

### Post by David26 on 2008-04-18
```
sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:d3:77:84
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.21 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

The first code gave nothing in return. I uninstalled the WiCD, and reinstalled gnome network manager. Yet still, only wired is working, wireless ain't. And I got a 5007EG and in the result above it is tagged as 5006. -_-.

---

### Post by chili555 on 2008-04-18
Please see: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)  especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themSo that means as long as you have the ethernet connected and have an IP address, which you do:```
ip=192.168.1.21 latency=64 link=yes
```Then NetworkManager will *not* activate your wireless.

Please disconnect the wire and do:```
sudo modprobe ath_pci
sudo ifconfig eth0 down
sudo iwconfig
```Did your wireless interface appear? ath0, perhaps? If so, do:```
sudo dhclient ath0
```Post back with some good news.

Wow, I love me some code tags!

---

### Post by David26 on 2008-04-19
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

I don't see any WiFi, not ath0 and not wlan0 or something like that.
BTW. I am running Ubuntu 64 Bit.

---

### Post by David26 on 2008-04-19
Well mates, I tried [http://www.mumblyworld.info/ubuntu/](http://www.mumblyworld.info/ubuntu/), acer_acpi. Yet no luck, it seems Ubuntu doesn't seem to regonize my WiFi Atheros card wich is build in. And this really makes me tired, because I am almost three days bussy trying to fix this. And I might consider to go back to windows again, because without WiFi, ubuntu is boring. I hope maybe in the future the boys and girls can include the WiFi drivers, all tutorials on the internet are not helping me any further. I tried acer_acpi, I tried ndiswrapper, I tried MadWiFi, all telling they work for my laptop. Adding my laptop to the line of supported hardware. But more people then me don't get it working :S. If anyone ever has a propper fix for it. Then tell me.

Beside that, the Acer_ACPI has given no error. Yet I dont get it working arghh... :S

---

### Post by David26 on 2008-04-19
WHen installing ndiswrapper i get error message when trying to run the driver.

```
david@david:~/wa/Drivers/XP-x64$ tail /var/log/messages
Apr 19 11:00:43 david kernel: [   52.018979] hda-intel: Invalid position buffer, using LPIB read method instead.
Apr 19 11:01:55 david kernel: [   97.931484] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Apr 19 11:01:55 david dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 19 11:01:57 david kernel: [   98.968660] NET: Registered protocol family 17
Apr 19 11:01:58 david dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr 19 11:01:58 david dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr 19 11:01:58 david dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 19 11:01:58 david dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 19 11:02:00 david kernel: [  100.086031] NET: Registered protocol family 10
Apr 19 11:02:00 david kernel: [  100.086202] lo: Disabled Privacy Extensions

```

---

### Post by David26 on 2008-04-19
Well, together with acer_acpi and ndiswrapper with 64 bit drivers from windows xp I finally can see wireles networks with the gnome network manager. I got it working, their is only one problem left, and that is connecting to the wireless networks. I am trying to connect to my home network, however it aint get connected -_-.

---

### Post by scottro on 2008-04-19
This popular (with lowend laptop makers) card gives a lot of problems in 64 bit.  I only got as far as you did, having iwlist show the networks but being unable to connect. 

One possible (UNVERIFIED!!) problem is that it uses the net5211 driver and I have seen some things saying it doesn't work with WPA 2.  I repeat that is unverified, but I never tried it on any other sort of network. 

With 32 bit, the madwifi driver usually works. I have my own page on it at [http://home.nyc.rr.com/computertaijutsu/rhwireless#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless#5007), if you decide to go the 32 bit route.  Atheros is apparently being quite reticent about working with the MadWifi people on it.  Several months ago, the ticket (1679) on MadWifi's site said they were in negotiations, but apparently, nothing has happened yet. 

One bright spot is that I found Mandriva's live "one" CD (32 bit though) is supporting the card out of the box.  That's the first distro I've seen that has managed to do this.  It may be connected to the fact that they now have an Asus EEE PC version, since that's the card ASUS uses.

---

### Post by David26 on 2008-04-20
```
http://ubuntuforums.org/showthread.php?t=759552
```

---

