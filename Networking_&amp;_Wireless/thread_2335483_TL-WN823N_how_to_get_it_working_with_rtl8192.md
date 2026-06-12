---
title: "TL-WN823N: how to get it working with rtl8192"
date: 2016-08-29
forum: Networking &amp; Wireless
---

### Post by QBuN@7jDAX8 on 2016-08-29
[B]Step 1
[/B]```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
```

Install the rtl8192eu-dkms package.

[B]Step 2
[/B]Run _lshw__ -class network_ and find the wireless interface [I](**enx18a6f7072dad** in my case)
[/I]
[B]Step 3
[/B]Run _sudo ifconfig enx18a6f7072dad up_ to get it up and running.

[B]Step 4
[/B]Restart the network manager: **sudo**[B] service network-manager restart


How I solved it:
[/B]
Downloaded the official drivers from their website:

```
sudo make
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.4.0-34-generic/build M=/home/vlad/TL-WN823N(EU)_V2_160315_Linux/Driver  modules
/bin/sh: 1: Syntax error: "(" unexpected
Makefile:1696: recipe for target 'modules' failed
make: *** [modules] Error 2

```

[B]I tried the following methods with no success:
[/B][URL="https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md"]rtl8192cu-fixes
[/URL][URL="https://www.raspberrypi.org/forums/viewtopic.php?t=148389"]some guy at raspberry pi forums compiling drivers
[/URL]
[B]What helped me ?
[/B][wireless-info]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385")

Even after plugging the stick in and out it would get recognized by _ifconfig_:
```
##### lsmod #############################

cfg80211              499712  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17897 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:72949534 (72.9 MB)  TX bytes:1916594 (1.9 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.
```
Ran _lsusb_, found the dongle:
```
[COLOR=#000000]Bus 001 Device 004: ID 2357:0109[/COLOR]
```

Googled some more, found this topic: [TP-LINK TL-WN823N Unable to connect to network]("https://askubuntu.com/questions/813443/tp-link-tl-wn823n-unable-to-connect-to-network")

Added this repository:
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
```
Install the rtl8192eu-dkms package afterwards.

Once it's installed, run _lshw__ -class network_:```
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 6c:62:6d:e8:02:1f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.18 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:29 memory:febc0000-febfffff ioport:ec00(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
**       logical name: enx18a6f7072dad**
       serial: 18:a6:f7:07:2d:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192eu multicast=yes wireless=unassociated

```

Now I have a network called **enx18a6f7072dad**. Run _sudo ifconfig enx18a6f7072dad up_ to get it up and running.

Now the last thing you need to do is restart the network manager: **sudo**** service network-manager restart**

---

### Post by kenlibero on 2017-03-08
[**[COLOR=#000000]Tuplad[/COLOR]**]("https://ubuntuforums.org/member.php?u=853719") I love you :D

In the last days I followed exactly the same path you did to make TL-WN823N-V2 work, but I was missing the last two commads (ifconfig up and network manager restart)
In my case the interface has a different name, but now is up and working.

I installed the rtl8192eu driver downloading it from here
[http://github.com/Mange/rtl8192eu-linux-driver](http://github.com/Mange/rtl8192eu-linux-driver)
instead of the repository you wrote, but I guess it's the same.

I confirm this good guide works for 4.4.0.64 kernel on linux mint 18.1 serena 64 bit.

Thank you so much for your sharing Touplad :)

---

