---
title: "Yet another RT2500 wireless usb problem"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Temujin_12 on 2008-01-12
I have a Belkin Wireless G USB network adapter (model: F5D7050 and FCC ID: K7SF5D7050A).  According to [this post]("http://ubuntuforums.org/showthread.php?t=273139&highlight=K7SF5D7050A#post1591182"), FCC ID K7SF5D7050A means it needs the rt2500 version of the driver.

I followed the [guide here]("http://ubuntuforums.org/showthread.php?t=400236") to download the rt2500 driver, compile it, load it into the kernel, blacklist other conflicting drivers, and configure the USB adapter to connect to a network.  Everything went just fine (no error messages) but I never see the light blink, scanning for networks always returns nothing, and trying to connect results in "no dhcpoffers received."

I see plenty of threads talking about how to fix particular errors in setting this up, but not any about how to determine what can cause the USB adapter to fail to work even though it's not throwing any errors (at least not in the console).

Here's my environment:

Wireless Router:
```
Model: Microsoft MN-700
Wireless Mode: G
Wireless network name (SSID): My Network
Channel:  11
MAC Address Filtering*: Enabled
Encryption type: 	WEP
Broadcast SSID: No
```
*Yes, I have the MAC address of this USB adapter (00:11:50:78:28:63) in the list of accepted MAC addresses and using this USB adapter to connect in Windows XP works fine.

Laptop (trying to connect):
```
Model: Compaq Presario 2100
OS: Wubi-installed xubuntu-7.04-alternate-i386
Wireless Adapter: Belkin Wireless G USB network adapter (model: F5D7050 and FCC ID: K7SF5D7050A)
```

Here's what I'm seeing:
$ ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:81:8B:62  
          inet addr:192.168.2.187  Bcast:192.168.2.255  Mask:255.255.255.0

          inet6 addr: fe80::20d:9dff:fe81:8b62/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1383 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1078 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:104113 (101.6 KiB)  TX bytes:87266 (85.2 KiB)

          Interrupt:11 Base address:0xe000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1065 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1065 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:105947 (103.4 KiB)  TX bytes:105947 (103.4 KiB)



wlan0     Link encap:Ethernet  HWaddr 00:11:50:78:28:63  

          inet6 addr: fe80::211:50ff:fe78:2863/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



wlan0:ava Link encap:Ethernet  HWaddr 00:11:50:78:28:63  

          inet addr:169.254.4.169  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


```

$lsusb
```
Bus 001 Device 003: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 001: ID 0000:0000 
```

I'm running the following to configure the USB adapter:
```
sudo ifconfig wlan0 down

sudo dhclient -r wlan0

sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid "My Network"

sudo iwconfig wlan0 key ffffffffffffffffffffffffff

sudo iwconfig wlan0 mode Ad-Hoc

sudo iwconfig wlan0 channel 11

sudo dhclient wlan0
```

When I run the last command, here's what I see:
```
Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/wlan0/00:11:50:78:28:63

Sending on   LPF/wlan0/00:11:50:78:28:63

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

```


Also, if I enable broadcasting of SSID in my router and try to scan for networks this is what I see:

$sudo iwlist wlan0 scanning

```
wlan0     No scan results

```

I've also tried to scan for wireless networks in hot spots that I know have several SSIDs being broadcasted.

This USB adapter works fine if I boot to Windows on that laptop.

Anyone know what steps to take from here?  Are there log files I can view or commands I can run to further investigate whether things are setup correctly?

Thanks for your help!

---

### Post by Digger78 on 2008-01-12
your using the wrong driver, i have an ASUS usb adapter (same chipset) you should be using RT2500usb.

I have attached the driver below.

removed the current driver with

```
sudo ndiswrapper -r rt2500
```

extract the driver folder  that i attached.

open a terminal in the extracted folder then do

```
sudo ndiswrapper -i rt2500usb
```

you may need to reload ndiswrapper

```
sudo rmmod ndiswrapper

sudo modprobe ndiswrapper
```

Hope this helps

---

### Post by Digger78 on 2008-01-12
Sorry, i just realised that you are not using ndiswrapper.

I would recommend downloading and compiling ndiswrapper and using the driver that i attached.

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.51.tar.gz?modtime=1197921854&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.51.tar.gz?modtime=1197921854&big_mirror=0)

---

### Post by Temujin_12 on 2008-01-12
Thanks Digger78, ndiswrapper worked!
I followed the sticky guide for getting ndiswrapper to work (making sure to blacklist the rt73 driver compiled previously).  I couldn't get the driver to install from the file you attached.  I [downloaded the driver from Belkin]("http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0") (mine was the 2xxx version), installed it on a windows system, copied those files to a directory on the laptop, then ran the ndiswrapper -i <drivername>.inf command to install it.

Out of curiousity, I also tried installing the Belkin driver on a linux box using wine and it completed the install and i had the same directory structure with all the files needed.  So if someone is in this situation and doesn't have a windows box, wine will work for extracting the files that you need.

I'm now up and running wirelessly!  :)

---

