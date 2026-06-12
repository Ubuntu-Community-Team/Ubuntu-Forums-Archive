---
title: "WUSB11 (Again)"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Not Your Raven on 2007-04-14
I know that I'm not supposed to post another thread about this, but I received no replies on my other thread. I apologize, as I only did this because I am incredibly frustrated. I searched the forums, and read nearly every post on getting a WUSB11 Linksys wireless adapter to work. I followed several different guides, none of which worked. I used ndiswrapper 1.41 to install the driver, and it installed fine. When I run lsusb, it shows my device. Ndiswrapper lists the driver as installed and the hardware as present. I added the following line to my network interfaces, under wlan0:
iface wlan0 inet dhcp

When I run iwconfig, it says "no wireless extensions" under wlan0. When I try to run this
iwlist wlan0 scan

It says: 
ERROR: Device does not support scanning

I am a complete noob with this, but it seems to me that the device is installed, but it is not associated with "wlan0" Maybe it goes by a different name.

Help is greatly appreciated.

---

### Post by Not Your Raven on 2007-04-16
Could I please just get one reply, even if it is just someone saying "Nobody has a clue what your problem is, sorry". I just want to know that someone has actually read the thread.

---

### Post by Floppyjoe on 2007-04-16
Please post your /etc/network/interfaces file.
```
sudo gedit /etc/network/interfaces
```
What version of Ubuntu are you using?

---

### Post by Not Your Raven on 2007-04-16
Thank you for responding! I will log in to Ubuntu and edit the results in to this post momentarily. I am running Ubuntu Edgy Eft 6.1, and I have an unsecured network.

EDIT: Here is the file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless-essid linksys

---

### Post by Floppyjoe on 2007-04-16
try adding:
```
wireless-channel 6 #where six is replaced with your router channel#
```
to your wireless interface.

---

### Post by RomeReactor on 2007-04-16
Hi. What is the output of running

```
sudo lshw -class network
```

in the terminal?

---

### Post by Not Your Raven on 2007-04-16
@Floppy Joe: I'm sorry, but I don't know what my router channel is, is there a simple way to find it. 

EDIT: Went to router page, and saw my channel was just a blank box, with no options to change it?

@ Rome Reactor: Ok this is what I got

sudo lshw -class network

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:2f:a5:71:19
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e800-e8ff iomemory:cffff400-cffff4ff irq:233
l@Computer:~$

---

### Post by Floppyjoe on 2007-04-16
Can you post the relevant output of:
```
lspci or lsusb
```

---

### Post by Not Your Raven on 2007-04-17
Results of lsusb:
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0461:4d09 Primax Electronics, Ltd 
Bus 002 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:009d Microsoft Corp. 
Bus 001 Device 005: ID 03f0:7204 Hewlett-Packard DeskJet 36xx
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 006: ID 0930:6540 Toshiba Corp. 
Bus 005 Device 001: ID 0000:0000  

Here is some more info for you:

Router model:Linksys BEFW11S4 Wireless B

Modem:Westell Model 2200

Adapter:Linksys WUSB11v4 Wireless B adapter.

Just to restate it, I can't see the router channel on my router page, it is just a blank box. My network is unsecured.

---

### Post by Floppyjoe on 2007-04-17
I think but am not positive that most routers are set to the default channel 6 to start with. It seems odd that you would not have an option to choos the channel.

---

### Post by Not Your Raven on 2007-04-17
I added the wireless channel as 6 and then restarted, but hen I still got nothing. It really seems to me that the device is not associated at all with "wlan0". When I try to scan with wlan0 "iwlist wlan0 scan", it says the thing about the pid file being present, which is supposed to happen according to the guides. Then it says "ERROR: device does not support scanning, bind socket to interface". Or something similiar to that. How can I associate my adapter with wlan0?

---

### Post by Floppyjoe on 2007-04-17
Are you sure wlan0 is the wireless interface? Maybe it is eth1. What is the output of :
```
iwconfig
```

---

### Post by Not Your Raven on 2007-04-17
iwconfig:

lo  no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions

The file got all weirdly formatted because I had to transport it to XP via a flash drive after reboot. I'm pretty sure the first one was "lo     no wireless extensions".
It used to be before I added the wireless SSID, etc, to my network interfaces file that a line like this would also appear when I ran iwconfig:
wlan0              no wireless extensions.

---

### Post by tturrisi on 2007-04-17
acdcording to this table, the wusb11 v4 is NOT supported in Linux.
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)
 It has an Ali chipset for which there are no linux drivers.
It *may* be possible to get it working using ndiswrapper.
Go here & use Edit > Find: ** Card: Linksys #[WUSB11v4], 802.11b, USB 1.1**
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
windows driver:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943540888B27&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943540888B27&displaypage=download#versiondetail)

---

### Post by Not Your Raven on 2007-04-17
Well I just realized the driver you linked me to was the same one I tried to install before. So I do not think there is a way to install this with Ubuntu. Thank you for the help, though.

---

