---
title: "Ubuntu 10.04, Dell Inspiron 1000 and no ethernet"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by uubooker on 2010-08-28
Greetings community!  In short, the laptop I just installed 10.04 onto can no longer detect and connect to the internet.  I recently did a clean install from 7.xx (wired ethernet worked, wireless did not) and figured the newer distro might be better.  While I have been using ubuntu on that laptop for a few years now, I still barely know my way around (the laptop is rarely used), hence the post here.  With this new problem, wireless still does not work (have been trying to get the drivers installed via flash drive but am running into roadblocks) and now the wired connection does not work.  At first the autoeth0 did not detect anything...after tweaking the settings to what my desktop says when connected, it thinks it is plugged in (the icon changes and says it is connected) but there is still no internet and no ability to download updates.  I'm pretty lost outside the most basic of commands and tasks, so any and all help pointing me toward greater understanding and a possible fix would be greatly appreciated!

---

### Post by mikewhatever on 2010-08-28
From a terminal window, can you post some info:

ifconfig
sudo lshw -C network

---

### Post by uubooker on 2010-08-28
Heres the feedback:

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:b8:04:95  
          inet addr:67.166.250.138  Bcast:67.166.255.255  Mask:255.255.248.0
          inet6 addr: fe80::20f:1fff:feb8:495/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6861242 (6.8 MB)  TX bytes:69272 (69.2 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122425 (122.4 KB)  TX bytes:122425 (122.4 KB)



[B]sudo lshw -C network
[/B]  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:b8:04:95
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=67.166.250.138 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1800(size=256) memory:e4003000-e4003fff memory:28000000-2801ffff(prefetchable)

This is with the ethernet cable plugged in and the connection "connected", but with no access to the network/internet.

---

### Post by mikewhatever on 2010-08-29
Interesting. Both outputs clearly show eth0 interface gets an ip address. Can you try pinging google.com and post the output too.

ping -c4 74.125.39.106

---

### Post by uubooker on 2010-08-29
"icmp_seq=1 Destination Host Unreachable" for each attempt...

Also, on the note of the IP it did not originally get an IP when I first connected it.  The IP and DNS etc it has now is what I plugged in based off what my desktop has when connected.  It obviously didn't work though lol.

---

### Post by uubooker on 2010-08-29
Short update...no real progress.  Tried the fix from this thread [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) but the process "failed to fetch" just about everything.  I tried installing the wireless drivers from a flash drive but again, failed to complete because it either could not fetch or download (with no connection) the required files.

---

### Post by mikewhatever on 2010-08-30
What if you undo the changes to the wired interface and leave it the default ghcp?

---

### Post by plucky on 2010-08-31
> **uubooker said:**
> Short update...no real progress.  Tried the fix from this thread [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) but the process "failed to fetch" just about everything.  I tried installing the wireless drivers from a flash drive but again, failed to complete because it either could not fetch or download (with no connection) the required files.

What drivers are you trying to install as you have not yet established that you have a wireless interface?

This is the output for the command "lspci" on my Dell Inpiron 1000
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
[color=red]02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/color]

```

The wireless card (in red) is actually a Netgear WG511 PCMCIA card plugged into the Cardbus,as my Dell Inspiron 1000 didn't ship with a wireless card.

From your command "sudo lshw -C network",no wireless card is displayed which leads me to think that there is no wireless card installed.

I would recommend getting the wired connection working.


Good Luck

---

### Post by uubooker on 2010-08-31
Went back to square one.  Mike, I reset the wired connection to default values (nothing) and plugged it in.  The little icon would swirl around for about 30 seconds and then say wired connection was disconnected.  I ran the most recent commands with that setup.  For Plucky, you're right, at the time that I ran the last set the network card was not plugged in, these last values have it in there.

What I don't get is that it seems to realize everything is there and how to work it, it just doesn't work :(


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:b8:04:95  
          inet6 addr: fe80::20f:1fff:feb8:495/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8009200 (8.0 MB)  TX bytes:83250 (83.2 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:176271 (176.2 KB)  TX bytes:176271 (176.2 KB)



sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:b8:04:95
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1800(size=256) memory:e4003000-e4003fff memory:28000000-2801ffff(prefetchable)
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:17
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:24000000-24001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:c6:40:d3:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg



lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by plucky on 2010-08-31
Open **System > Preferences > Network Connections** and in the window that opens select **Wired**.

If there is already a connection,select it and then **Edit**,if there isn't a connection showing select **Add**.

Then under IPV4 settings tick the connect automatically box and make sure **Automatic DHCP ** is selected in the Method box.

Then select **Apply** and see if a connection is established.

If that works, then open **System > Administration > Hardware Drivers** and see what downloads.

Good Luck

---

### Post by mikewhatever on 2010-08-31
uubooker, if what plucky had suggested doesn't work, run the commands below, then grab the syslog.txt and dmesg.txt from the Desktop and attach to your next post.
```

cat /var/log/syslog > ~/Desktop/syslog.txt

dmesg > ~/Desktop/dmesg.txt

```

Hopefully, that would provide some clues.

---

### Post by uubooker on 2010-08-31
Thanks for the advice Plucky, but I already had the connection set up as such so not much new from there :-(

To mike: for some reason Terminal did not want to write to a named file that didn't yet exist, so I did this the old fashioned way (hopefully the file attachment works for me, otherwise we're looking at some loooong posts haha)...looks like the dmesg file was too big, so I threw both of them into a zip (too much of a hassle? probably).  Sorry bout that!

---

### Post by mikewhatever on 2010-09-01
Here is an old thread with the same card and, what looks like, a similar problem. Do try the commands suggested in post 9:

sudo ifconfig eth0 down hw ether 00:E0:18:B3:A0:F7
sudo ifconfig eth0 up 

but don't edit /etc/network/interfaces, as suggested later.

---

### Post by uubooker on 2010-09-01
The above commands didn't seem to do much for me...no visible change and no connection even after a restart.  The little spinning icon just spins for a minute then reports that it is disconnected :-(

Which thread was supposed to be linked in that last post?

---

### Post by mikewhatever on 2010-09-02
Forgot to post the link, sorry.
[http://www.linuxquestions.org/questions/linux-hardware-18/sis900-pci-ethernet-wont-connect-to-network-617944/](http://www.linuxquestions.org/questions/linux-hardware-18/sis900-pci-ethernet-wont-connect-to-network-617944/)

---

