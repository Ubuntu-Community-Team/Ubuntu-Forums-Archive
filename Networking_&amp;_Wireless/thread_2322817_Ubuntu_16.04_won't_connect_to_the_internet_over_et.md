---
title: "Ubuntu 16.04 won't connect to the internet over ethernet"
date: 2016-04-30
forum: Networking &amp; Wireless
---

### Post by EoRaptor013 on 2016-04-30
So, two years later... hope somebody sees this. I just installed a new AMD FX-8350, and Gigabyte 990FX motherboard after my Intel LGA 1155 i7 failed. I enabled IOMMU during the very first boot. Ubuntu 16.04 did not detect the internet during installation, nor will it connect now that I've got everything put together. 

Output from lshw:

```
  *-network               
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 10
       serial: 40:8d:5c:e0:27:93
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:39 memory:fe300000-fe33ffff ioport:d000(size=128)
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 06
       serial: c8:3a:35:d2:04:2c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:27 ioport:c000(size=256) memory:fe100000-fe100fff memory:da100000-da103fff memory:fe120000-fe13ffff


```

I don't have ethtools on this install. Ifconfig says it can't find eth0.

EDIT to add:

Just tried ifconfig without parameters and got this:
```

enp5s0    Link encap:Ethernet  HWaddr 40:8d:5c:e0:27:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

```

Hope this helps.

EDIT to add:
Crazy thought, is it possible that as a regular user, I don't have permission to the network device?
Any help greatly appreciated!

---

### Post by EoRaptor013 on 2016-04-30
One more edit. I found ethtool and here's the output:

```

Cannot get device settings: no such device.
Cannot get link status: no such device.

```

So the left hand ethtool has no idea what the right hand ifconfig, or lshw, are doing.


Thanks.

---

### Post by jeremy31 on 2016-04-30
Posts moved to a new thread.

See if ```
systemctl restart NetworkManager.service
```
helps this at all as there seems to be some new Network Manager bugs involving the renaming of interfaces

---

### Post by EoRaptor013 on 2016-04-30
Jeremy, I gave it a shot and this is what I get:

Failed to restart NetworkManager.system.service: unit NetworkManager.system.service not found. 

As the man said, "That can't be good." But, maybe a clue?

Thanks for getting back to me.

---

### Post by jeremy31 on 2016-04-30
Is this on a server without a desktop environment?

---

### Post by EoRaptor013 on 2016-04-30
Nope, straight-forward Desktop installation from the AMD-64 image. I do wonder if this is a reason I should have paid more, but stuck with the tried-and-true Intel setup. Of course, I would have paid more than twice as much...

Thanks again.

---

### Post by jeremy31 on 2016-04-30
Both of the ethernet cards are supported by the results.  I dont have any ethernt available, hopefully somebody else can help you further it may help to post
```
dpkg -l | grep network
```

---

### Post by EoRaptor013 on 2016-04-30
lots of network packages. I'd try dpkg -i but don't know which package to try and build.

---

### Post by wildmanne39 on 2016-04-30
Your thernet card is using the 8169 driver but needs the 8168, usually still connects under this situation but goes so slow it will not download anything.
Please run the wireless script in my signature and it will tell us a little information about your ethernet connection just enough to know if my theory is correct.
Thanks

---

### Post by EoRaptor013 on 2016-04-30
After posting to a two year old thread, I'm trying a new thread. 
I did a memory-stick install of xenial, to newly purchased Gigabyte 990FX motherboard, with AMD FX8350 CPU. The install could not detect a network, even though the cable was connected to eth0. The system didn't do any better connecting to the internet, or even my local network, after installation. Here's the detecting I've done so far (HT to Jeremy31).

Output from lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 10
       serial: 40:8d:5c:e0:27:93
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:39 memory:fe300000-fe33ffff ioport:d000(size=128)
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 06
       serial: c8:3a:35:d2:04:2c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:27 ioport:c000(size=256) memory:fe100000-fe100fff memory:da100000-da103fff memory:fe120000-fe13ffff

```

Output from ethtool eth0:
```

Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

```

Finally, output from dpkg -l | grep network
```

ii  glib-networking:amd64                      2.48.0-1                                            amd64        network-related giomodules for GLib
ii  glib-networking-common                     2.48.0-1                                            all          network-related giomodules for GLib - data files
ii  glib-networking-services                   2.48.0-1                                            amd64        network-related giomodules for GLib - D-Bus services
ii  ifupdown                                   0.8.10ubuntu1                                       amd64        high level tools to configure network interfaces
ii  iproute2                                   4.3.0-1ubuntu3                                      amd64        networking and traffic control tools
ii  iputils-ping                               3:20121221-5ubuntu2                                 amd64        Tools to test the reachability of network hosts
ii  iputils-tracepath                          3:20121221-5ubuntu2                                 amd64        Tools to trace the network path to a remote host
ii  libnm-glib-vpn1:amd64                      1.1.93-0ubuntu4                                     amd64        network management framework (GLib VPN shared library)
ii  libnm-glib4:amd64                          1.1.93-0ubuntu4                                     amd64        network management framework (GLib shared library)
ii  libnm-util2:amd64                          1.1.93-0ubuntu4                                     amd64        network management framework (shared library)
ii  libproxy1-plugin-networkmanager:amd64      0.4.11-5ubuntu1                                     amd64        automatic proxy configuration management library (Network Manager plugin)
ii  libqt4-network:amd64                       4:4.8.7+dfsg-5ubuntu2                               amd64        Qt 4 network module
ii  libqt5network5:amd64                       5.5.1+dfsg-16ubuntu7                                amd64        Qt 5 network module
ii  net-tools                                  1.60-26ubuntu1                                      amd64        NET-3 networking toolkit
ii  netbase                                    5.3                                                 all          Basic TCP/IP networking system
ii  network-manager                            1.1.93-0ubuntu4                                     amd64        network management framework (daemon and userspace tools)
ii  network-manager-gnome                      1.1.93-1ubuntu1                                     amd64        network management framework (GNOME frontend)
ii  network-manager-pptp                       1.1.93-1ubuntu1                                     amd64        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                 1.1.93-1ubuntu1                                     amd64        network management framework (PPTP plugin GNOME GUI)
ii  tcpdump                                    4.7.4-1ubuntu1                                      amd64        command-line network traffic analyzer

```

I have a ton of work to do this weekend (I'm sending this from my wife's computer), so any help at all will be appreciated.

Thanks!

Randy

---

### Post by EoRaptor013 on 2016-04-30
I'd like to do that, but if the computer won't connect to the tubez, how do I? The only thing that has a connection to the internet is my wife's Windows 8.1 machine. Is there a way to do it from there and save to a thumb-drive?

Thanks!

---

### Post by EoRaptor013 on 2016-04-30
PS:  Also, just for my understanding, how does wireless information help with an ethernet, wired, connection?

Thanks!

---

### Post by wildmanne39 on 2016-04-30
Here is a link with the directions for using the script without internet access.
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385)
There is just a little ethernet information collected in the wireless script just enough to let me know if I am correct, if I am I will see if there is an update driver for 16.04 yet.

---

### Post by $yl9pAR%t on 2016-04-30
Ubuntu 16.04 brings new names for network because of systemd. I see you have "[COLOR=#000000][FONT=Ubuntu Mono]enp5s0" and "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]enp7s0".

When it comes to ethtool, you can run this:

```
ethtool enp5s0
```

or

```
ethtool enp7s0
```[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
but I do not know if it will help you.[/FONT][/COLOR]

---

### Post by EoRaptor013 on 2016-04-30
mefisto888, 

Thanks. Well, ethtool now sees the adapter, and determines that it's linked (meaning the cable is plugged in, I'm guessing). 

Unfortunately I still can't get to the internet.

```

	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Current message level: 0x000060e4 (24804)
			       link ifup rx_err tx_err hw wol
	Link detected: yes

```

---

### Post by bab1 on 2016-04-30
What do you get from this command```
ifconfig -a
```

---

### Post by wildmanne39 on 2016-04-30
"Please do not post duplicates, it dilutes community effort. Threads merged"

---

### Post by EoRaptor013 on 2016-04-30
Sorry. I'm anxious about all the work I have to do. I blew-up my computer Thursday, and bought this AMD stuff that didn't "just work." But I really couldn't afford to replace my old i7. They don't make the LGA 1155 form-factor any more, and all the motherboards now require DDR4 RAM. I was looking at nearly $700 to get back basically what I had. 

I guess one gets what one pays for.

---

### Post by EoRaptor013 on 2016-04-30
Here's ifconfig -a:

```

enp5s0    Link encap:Ethernet  HWaddr 40:8d:5c:e0:27:93  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:326463 (326.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:16 

enp7s0    Link encap:Ethernet  HWaddr c8:3a:35:d2:04:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:44180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:3269184 (3.2 MB)  TX bytes:3269184 (3.2 MB)


```

Wish I could figure out what's going on here. Seems like all the pieces are there, but nothing's glued together. 

I'll have to let it be for the night. Try again in the morning.

---

### Post by bab1 on 2016-04-30
> **EoRaptor013 said:**
> Here's ifconfig -a:

```

enp5s0    Link encap:Ethernet  HWaddr 40:8d:5c:e0:27:93  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:326463 (326.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:16 

[COLOR="#FF0000"]enp7s0    Link encap:Ethernet  HWaddr c8:3a:35:d2:04:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/COLOR]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:44180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:3269184 (3.2 MB)  TX bytes:3269184 (3.2 MB)


```

Wish I could figure out what's going on here. Seems like all the pieces are there, but nothing's glued together. 

I'll have to let it be for the night. Try again in the morning.All of your focus has been on is the physical hardware.  The OS sees the hardware interface you call eth0 (see red above).  The naming convention is different but the OS and most apps understand that. It does need to be configured however.   There are several ways that this is done.  For most folks it is as easy as opening Network-Manager (Network Connections)  and making sure that the Ethernet connection is set to Automatic (DHCP).

---

### Post by EoRaptor013 on 2016-05-01
OK, so I switched the cable to the add-on card, enp7s0, but no joy. I'm on the verge of removing the AMD CPU and motherboard, and paying the premium for an Intel CPU, motherboard, and RAM. I don't know much (as in nothing) about hardware configuration, but this shouldn't be that hard. While looking around yesterday, I noticed that in dev/block(?) -- don't remember where right now -- but there was nothing in the network interfaces folder. In my ignorance, I have no idea if that's significant.

---

### Post by EoRaptor013 on 2016-05-01
OK, so I am definitely using the r8169 driver. How do I go back to the r8168 in a machine that cannot connect to the internet. Can I download a deb package from windows onto a thumb-drive? If so, where do I find the package?

Thanks.

---

### Post by bab1 on 2016-05-01
> **EoRaptor013 said:**
> OK, so I switched the cable to the add-on card, enp7s0, but no joy. I'm on the verge of removing the AMD CPU and motherboard, and paying the premium for an Intel CPU, motherboard, and RAM. I don't know much (as in nothing) about hardware configuration, but this shouldn't be that hard. While looking around yesterday, I noticed that in dev/block(?) -- don't remember where right now -- but there was nothing in the network interfaces folder. In my ignorance, I have no idea if that's significant.
I'm telling you that the system is fine just as it is.  Both NIC's are displayed.  You just need to either; configure the one of interfaces ( enp5s0 or enp7s0) using the Network-Manager app or; manually via the configuration file /etc/network/interfaces.

Don't mess with the /dev files.  There is no reason to do that.  Those files are for the system itself to interface with the hardware.

I would not spend the money on more hardware as what you have will work just fine once you *_configure_* it.

Here is my ifconfig output.  Note the configured IP address in red.  It is the part you need to setup```

enp2s0    Link encap:Ethernet  HWaddr 00:1d:ba:88:2d:2e  
[COLOR="#FF0000"]          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:baff:fe88:2d2e/64 Scope:Link[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8134 (8.1 KB)  TX bytes:11138 (11.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:479001 (479.0 KB)  TX bytes:479001 (479.0 KB)


```
The /etc/network/interfaces file looks like this```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```...the lack of an Ethernet or Wifi interface is because Network Manager is handling the configuration so it is not needed in this conf file.

In short, the hardware is there, you just need to configure it.  Do you know how to do that?  Do you know how to use Network Manager?

---

### Post by bab1 on 2016-05-01
> **EoRaptor013 said:**
> OK, so I am definitely using the r8169 driver. How do I go back to the r8168 in a machine that cannot connect to the internet. Can I download a deb package from windows onto a thumb-drive? If so, where do I find the package?

Thanks.
Note that the driver will not configure the interface.  The driver is only to describe the chipset (hardware) to the OS.  I makes the hardware available for configuration which you already have.  What makes you think you need the earlier driver?

---

### Post by wildmanne39 on 2016-05-01
Because It looks like his ethernet card is : Ethernet interface product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller and ubuntu has been installing the wrong driver for that card for years. I am not saying there are not other issues but when he gets connected with that card his internet will be unusuable.

That is why I asked him to post the output of the wireless script it will give us some useful information on his issue, even though the script is for wireless issues.

---

### Post by bab1 on 2016-05-01
> **Wild Man said:**
> Because It looks like his ethernet card is : Ethernet interface product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller and ubuntu has been installing the wrong driver for that card for years. I am not saying there are not other issues but when he gets connected with that card his internet will be unusuable.

That is why I asked him to post the output of the wireless script it will give us some useful information on his issue, even though the script is for wireless issues.
This may be so, and I have not read all the posts on the duplicate posting, but the host has 2 interfaces.  The one on the mobo and the one the OP installed.  Are both using the same driver type?

---

### Post by EoRaptor013 on 2016-05-01
Thanks Wild Man. I did run the script, but I'm so ignorant, I can't seem to copy the results to a thumb-drive so I can bring it to this machine to post. For some reason, all the thumb drives I used to post output yesterday, are now are owned by root today. Further, Even though I did a chown myName:myName on the identifier, in /mnt (or was it /media?), I still can't write to them. Most discouraging. 

I'll try again in a few minutes. 

Thanks.

---

### Post by wildmanne39 on 2016-05-01
> **bab1 said:**
> This may be so, and I have not read all the posts on the duplicate posting, but the host has 2 interfaces.  The one on the mobo and the one the OP installed.  Are both using the same driver type?
Yes I know he has two ethernet cards and no they do not use the same driver.

Like I said I am not saying that is the only issue but it is going to be most likely once it is connected.
I have real life issues today so I am out and I am sure you can get him going.

---

### Post by bab1 on 2016-05-01
> **EoRaptor013 said:**
> Thanks Wild Man. I did run the script, but I'm so ignorant, I can't seem to copy the results to a thumb-drive so I can bring it to this machine to post. For some reason, all the thumb drives I used to post output yesterday, are now are owned by root today. Further, Even though I did a chown myName:myName on the identifier, in /mnt (or was it /media?), I still can't write to them. Most discouraging. 

I'll try again in a few minutes. 

Thanks.
Most of the time you can't use chmod or chown on a thumb drive.  The mount point ownership is not relevant.

---

### Post by EoRaptor013 on 2016-05-01
Well, it's amazing what you can do from the command-line when you are root...

Here's the wireless info:

```


########## wireless info START ##########

Report from: 01 May 2016 05:24 MDT -0600

Booted last: 01 May 2016 00:00 MDT -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, nopat, splash, plymouth:debug=1

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd Killer E220x Gigabit Ethernet Controller [1458:e000]
	Kernel driver in use: alx

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
Bus 002 Device 006: ID 1532:0032 Razer USA, Ltd 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1532:010d Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:0811 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF]>  
          inet6 addr: fe80::2bf:a3fc:4cf4:f064/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:846 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp5s0    no wireless extensions.

enp7s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root       830     1  0 04:33 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       679da919-1f48-4b57-b3e6-03363f97a709
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/29
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   679da919-1f48-4b57-b3e6-03363f97a709 | Wired connection 2

GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Killer E220x Gigabit Ethernet Controller
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp5s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Denver (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp5s0    no frequency information.

enp7s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp5s0    Interface doesn't support scanning.

enp7s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 2175.002097] r8169 0000:07:00.0 enp7s0: link up (repeated 7 times)

########## wireless info END ############



```

As I noted a few minutes ago, the driver is, indeed, r8169. There are several posts in the wild suggesting this driver is flaky. I'd, at least, like to try using the prior version before I spend a wheelbarrow of cash to get back to an Intel setup. I have high confidence in the Intel stuff mainly because I was running 16.04 successfully on that setup before I burned up the CPU. (Just to tell tales on myself, I installed one of those self-contained water cooling systems into that machine. Thinking I am such a smart man, I put a fan on both sides of the radiator, thus supposedly greatly  increasing the airflow. (Can you guess where this is going?) When I took the system apart, I noticed an interesting thing: the fans were blowing against each other -- push me push me, instead of push me pull me.) 

Thanks to both of you, for helping.

---

### Post by jeremy31 on 2016-05-01
What is the problem with the other ethernet connection?  I see it uses the alx module and I finally found something on it.  Try changing the MTU in Network Manager for that to 8192, save connection settings and reboot

---

### Post by EoRaptor013 on 2016-05-01
Nada. I blame it all on my mother

board.

---

### Post by bab1 on 2016-05-01
> **EoRaptor013 said:**
> Nada. I blame it all on my mother

board.
Blame what?  All you need to do is assign an IP address, b'cast address and gateway address to that interface.  The resolution is up to you.  So far there doesn't seem be any problem with Ubuntu or the hardware.

---

### Post by wildmanne39 on 2016-05-01
Reboot your router and then your computer does network manager find your network?
It has been reported in 16.04 that secure boot has to be off for some people to connect.
I have used AMD products for more then ten years and I have never had a problem because of AMD.

---

### Post by bab1 on 2016-05-01
> **Wild Man said:**
> Reboot your router and then your computer does network manager find your network?...or see if a mobile device (tablet or cell) can connect.  The dhcp server in the router is the same for both wifi and wired.

---

### Post by EoRaptor013 on 2016-05-01
I've done a hard reboot most of the times that I'ved changed something. That always seems to be the best approach. 

After the last hard reboot, I set a static IP of 10.0.0.20, which I am pretty confident isn't in use. For both DHCP and Gateway, I used 10.0.0.1, which is the IP for my cable router. I got those values from the Win machine. I don't see what the broadcast value is on the Win machine, nor do I see where to set it on the Linux box. 

In any event, given the values above, I did another hard-reboot -- meaning a cold-start -- but nothing has changed. 

As always, I greatly appreciate the time you all have spent on this.

---

### Post by bab1 on 2016-05-01
> **EoRaptor013 said:**
> After the last hard reboot, I set a static IP of 10.0.0.20, which I am pretty confident isn't in use.  For both DHCP and Gateway, 

Where did you do this?
> 
I used 10.0.0.1, which is the IP for my cable router. 
You need a different IP address from that of the router.  Each host has a unique address in the range of the network.
> 
I got those values from the Win machine. I don't see what the broadcast value is on the Win machine, nor do I see where to set it on the Linux box. 
The broadcast IP can be determined by the subnet mask.  The broadcast IP is set in the same place as the other IP addresses.  What is the subnet mask for the network?

---

### Post by $yl9pAR%t on 2016-05-01
To get some info about your network settings, run cmd on your Windows machine and give us output of:

```
ipconfig /all
```

Edit:

1. In case if you would not know what I am talking about.

[http://windows.microsoft.com/en-us/windows/command-prompt-faq#1TC=windows-8](http://windows.microsoft.com/en-us/windows/command-prompt-faq#1TC=windows-8)

2. When you installed OS, did Ubuntu installer inform you there were not internet connection?

Edit-2:

If you want to tinker with this Realtek driver, look here

[http://ubuntuforums.org/showthread.php?t=2318953](http://ubuntuforums.org/showthread.php?t=2318953)

---

### Post by EoRaptor013 on 2016-05-03
Sorry, missed this post. To answer your questions, yes I know how to configure a network interface, and yes, I know how to use Network Manager, and finally,  yes I tried configuring the card directly. Oh, and yes I know the hardware is there; output that I've posted proves it's there and recognized. Nevertheless, I cannot connect to the internet. If you're interested, you can see my last post to this thread for what I did.

Thank you for the effort.

---

### Post by EoRaptor013 on 2016-05-03
I would have sworn I posted this already, but...

As I mentioned in one or two posts in this thread, I had a pile of work that I had to get done, it required internet access, and I didn't have time to keep fiddling around. So, I bit the bullet, got another wheelbarrow of cash, returned the AMD FX8350 CPU, and Gigabyte mobo, and bought an Intel i7 6700, and a Gigabyte Z170X-UD3 mobo. I stuck in my thumb-drive, clicked install, and was off to the races. As I would have expected, it "Just Worked." 

Note that both mobo's were from Gigabyte. So, whatever the problem, it's not an inherent issue with Gigabyte. The particular mobo, FX990-A, and AMD processor wouldn't connect to the internet despite a great-deal of RTFM on my part, and even more help from folks here. The Gigabyte Z170X-UD3, and Intel processor, did connect to the internet during install, and continued to connect once install was complete. 

Maybe the community and I might have solved this problem over time, but I didn't have the time. 

So it goes.

---

### Post by bab1 on 2016-05-04
So mark the thread "solved" if you will, and we all will be done with it.

---

