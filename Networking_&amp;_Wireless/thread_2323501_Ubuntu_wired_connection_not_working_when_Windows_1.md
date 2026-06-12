---
title: "Ubuntu wired connection not working when Windows 10 works."
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by Stephen_Patrick_Shellard on 2016-05-05
Whilst doing some work on the wiring of my home wired network, I have developed a problem where Ubuntu 15.10  is unable to connect via ethernet.  There are - to me - a number of very puzzling features of this situation.  Firstly,  my Ubuntu 15.10 dual boots with Windows 10, and the Windows 10 ethernet connection, sharing the same wiring and interface, does not have a problem. Secondly,  I had a DVD with Ubuntu 15.10 and booted into a live version running from the DVD.  Again this results in no Internet connection via ethernet.  This evening I bought a beta version of 16.04 on DVD and again booted up using this disc, with the same result.  

I have been watching the small neon lights on the ethernet connection on the reverse of the computer as it boots up.  These flash to begin with - indicating a connection.  They continue to flash until the GRUB menu appears and for a short time thereafter, if I select Ubuntu 15.10.  Then the lights stop flashing and when the boot sequence is complete, network manager tells me that a network cable is unplugged.  Needless to say this is not the case.  Selecting Windows 10 on the other hand results in a continuous flashing of the neons until the boot sequence is complete at which point the Internet is available. 

It is important to point out that I have been using Ubuntu 15.10 since it first came out, without any difficulty of this kind.  Other devices on the wired network continue to work.  My wireless network continues to work [I access these via my android phone and on the chromebook I am using for this post]  This is a recent problem, possibly associated with  me plugging and unplugging connections from the router  in order to determine which cable was connected to which device on my network.  

My connection is superfast broadband.  My router is a netgear  [COLOR=#000000][FONT=Arial]**D6400** .   [/FONT][/COLOR]

---

### Post by edwin31 on 2016-05-06
does the wifi work from ubuntu?

---

### Post by Stephen_Patrick_Shellard on 2016-05-06
There is no wifi on my Ubuntu computer.  It purely has a wired connection.  Thank you for your interest.

---

### Post by jeremy31 on 2016-05-06
Please post the result of ```
lspci -nnk | grep -iA2 net; lshw -c net
```

It will provide needed information

---

### Post by Stephen_Patrick_Shellard on 2016-05-07
Here is the output from this code:

> 04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:8505]
    Kernel driver in use: r8169
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 09
       serial: 08:60:6e:d8:ac:94
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.




I note the warning to "run this programme as superuser"  and so entered the same line of code as a superuser, but the same warning appears and the output - to my eye -  is the same, so presumably this warning means something different than what I suppose.

---

### Post by Stephen_Patrick_Shellard on 2016-05-09
in the meantime I have been trying a few other things, but so far without success.

> sudo ifdown enp4s0   && sudo ifup ep4s0

This generates a sequence of information concluding with a series of almost identical lines:

> DHCPDiscover on enp4s0 to 2555.255.255.255  port 67  interval 3  (xid=0x724a224)

The first part of this line repeats about 20 times  with slight variation before concluding

> No DHCPOFFERS received
No working leases in persistent database - sleeping

Again I will reiterate:  this ethernet interface works fine with Windows 10 installed on the same machine, but fails to connect to the internet via installed 15.10 or via a live DVD.

---

### Post by jeremy31 on 2016-05-09
```
DHCPDiscover on enp4s0 to 2555.255.255.255 port 67 interval 3 (xid=0x724a224)
```

I think that is a typo, please post result for ```
ifconfig
``` and the results from the wireless script, link in my signature may help

---

### Post by Stephen_Patrick_Shellard on 2016-05-10
:~$ ifconfig
enp4s0    Link encap:Ethernet  HWaddr 08:60:6e:d8:ac:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:433540 (433.5 KB)  TX bytes:433540 (433.5 KB)

---

### Post by Stephen_Patrick_Shellard on 2016-05-12
Just a couple of points regarding the above.  First of all I did take a look at the Wireless Script link as suggested by Jeremy 31, but can see no relevance as there is no wireless interface on the computer to which I am referring.  The problem is with the ethernet connection.

I have been attempting many things, admittedly from a basis of little understanding of what I am doing, but the most hopefully so far seems completely bizarre to me.  When I enter the following code:

```
sudo ip link set enp4s0 down
```

after a second or two I get blinking lights at the ethernet socket on the computer.  [Steady orange, blinking yellow]  However this lasts only for a few minutes and if I follow up with ```
sudo ip link set enp4s0 up
```   immediately dissapears.   Also, regardless of presence of blinking lights I am unable to connect either to the Internet or router. I would also say that sometimes I only get the blinking yellow neon - no steady orange.  

This suggests some kind of intermittent failure with the interface and yet it consistently connects when I boot up in Windows 10.

---

### Post by jeremy31 on 2016-05-12
Do you have static DNS settings in Windows that you haven't set in Ubuntu?

---

### Post by Stephen_Patrick_Shellard on 2016-05-12
No. DHCP for both.
I do have reserved addresses set on my router related to Mac addresses. That has always worked fine and seems necessary to make my sonos music system function smoothly.

---

### Post by Stephen_Patrick_Shellard on 2016-05-13
It occured to me that the problem [of the failure of my ethernet connection in 15.10]could be related to the changes in recent versions to the set up to the ethernet interface such as for example the change to naming from eth0 to  [COLOR=#000000]enp4s0.  With this thought in mind I sought out an earlier version of Ubuntu on DVD [Ubuntu 12.04 or 12.10 - can't remember which]  and attempted to boot up from this. Once again there was no network connection when running from the disk.[/COLOR]

[COLOR=#000000]With a problem as persistent as this I would by this stage be considering a reinstallation but if it is not possible to establish a network connection via a live DVD, this would suggest to me that the problem is hardware related, and in this case, as the Ethernet socket is integral to the motherboard of the computer,  only a new interface or a new computer will solve the problem;  however, this conclusion is not supported by the fact that  the same computer continues to boot into Windows and connect to the Internet without any obvious problem. 

Advice welcome.[/COLOR]

---

### Post by jeremy31 on 2016-05-13
It could be an issue with the driver.  Download 

[http://packages.ubuntu.com/wily/all/r8168-dkms/download](http://packages.ubuntu.com/wily/all/r8168-dkms/download)

And find the dkms deb file on the live dvd/usb in /pool/main/d/dkms
Double click on the file name and it should install.  You will need to use a usb drive to transfer the r8168-dkms file to Ubuntu, then double click to install

Reboot

---

### Post by Stephen_Patrick_Shellard on 2016-05-13
This has worked, and whilst I am cautious as regards the stability of my system, given the amount of tinkering I have been doing over the past few days, but undoubtedly, I currently have an Internet connection on my previously unconnected system. Thank you so much for your support.

---

### Post by jeremy31 on 2016-05-13
Awesome, enjoy and please use thread tools at the top of the page to mark as solved

---

