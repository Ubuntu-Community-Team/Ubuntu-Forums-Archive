---
title: "Wireless doesn't work, fresh ubuntu 8.04 install"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Jmiller3414 on 2008-06-06
I just installed Ubuntu 8.04 on my laptop, updated it by pluggin it right into the router,
but for some reason I can't pick up any wireless connection.


I am using my laptop, it's a [ **Toshiba Satellite A215 - S4757 **]


Here is the info I get when I run **sudo lshw -C network**,



  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1c:b5:a9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
jmiller@jmiller-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1c:b5:a9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0



**I am a newb with ubuntu** lol, so please use **user friendly** words and step by step instructions that are **simple** to follow.

In the mean time i'll sit back grab some :popcorn: and enjoy a few episodes of Stargate Atlantis.
[B]
Thanks in advance,[/B]
      Jonathan Miller

---

### Post by Jmiller3414 on 2008-06-06
Grr, still working on it with no success, any and all help would be appreciated.

](*,):wink:

---

### Post by Jmiller3414 on 2008-06-06
Agh, still no progress.

---

### Post by sosipator on 2008-06-06
my problem is identical:

this is what I get in the console (about the same)

> sosipator@sosipator-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:fe:24:19
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
sosipator@sosipator-laptop:~$ 


I would appreciate very much if somebody gives some ideas here.

---

### Post by luwenhua on 2008-06-06
me too!

---

### Post by Quantumstate on 2008-06-06
Oh man, where to start?

Those of us who've slogged Linux for ten years just know the value of study and understanding.  We are used to the idea that you end up having to understand everything about everything, before you can get anything working.

These gay operating systems that do everything for you, are for the shoe salesmen of the world.  Used to be, Linux required an IQ north of 140, but not any more.

{gears up for a lecture}

... ah, fsck it.

---

### Post by Cup of Squirrels on 2008-06-06
> **Quantumstate said:**
> Oh man, where to start?

Those of us who've slogged Linux for ten years just know the value of study and understanding.  We are used to the idea that you end up having to understand everything about everything, before you can get anything working.

These gay operating systems that do everything for you, are for the shoe salesmen of the world.  Used to be, Linux required an IQ north of 140, but not any more.

{gears up for a lecture}

... ah, fsck it.

Seems odd that a personal computer, that is designed to make our lives easier and perform impossible tasks in milliseconds, is being bashed for DOING something for you.

;)

---

### Post by Quantumstate on 2008-06-06
You are in the Free community.  You're an OSS boy now.

Time to reset expectations and do a little study and work.  Or else go back to Gatesland corporate feudalism.

---

### Post by Naif.1 on 2008-06-06
Me too, I am having the same problem, please help. 

I was going to start a new thread.

Thanks in advance.

---

### Post by Cup of Squirrels on 2008-06-06
> **Quantumstate said:**
> You are in the Free community.  You're an OSS boy now.

Time to reset expectations and do a little study and work.  Or else go back to Gatesland corporate feudalism.

Simply here to open my mind - I've had years of bashing from my slightly more elitist friends for calling myself a geek and not using Linux - you are right, if something is free it can never be expected to be of the same quality of something that costs....!

But I will refrain from debate here, you're right - I'm in the Free community, and I am only here for some simple help.

Seems odd that I'll be doing my research on a Windows OS so I can eventually make my Linux OS do the same thing.


...;p

---

### Post by Quantumstate on 2008-06-06
Gotta start somewhere.

I started on the DOS bulletin boards 25 years ago, while during the day making my fortune in real estate and supporting my family. 

(Linux=Security)

Those who can't be bothered to study and learn, are only a burden.  And should go away.

You though Cup, I hope will stay.

---

### Post by Cup of Squirrels on 2008-06-06
> **Quantumstate said:**
> Gotta start somewhere.

I started on the DOS bulletin boards 25 years ago, while during the day making my fortune in real estate and supporting my family. 

(Linux=Security)

Those who can't be bothered to study and learn, are only a burden.  And should go away.

You though Cup, I hope will stay.

Well, after years of being "spoon fed" answers from Windows, compared to Linux, this all seems quite a steep learning curve ;)

For now, I just need to work out why my wireless card refuses to connect to my network

And don't worry, I will do everything I can do stand on my own two feet here - just ignore the thread I posted below! ;)

Thankyou for the support ;p

---

### Post by geezerone on 2008-06-06
> **Quantumstate said:**
> ...Those who can't be bothered to study and learn, are only a burden.  And should go away...

That is not the correct attitude of the Ubuntu community.

Regarding the O.P., take a look at [THIS]("http://ubuntuforums.org/showthread.php?t=662877") post about Atheros wireless chipsets.

---

### Post by Quantumstate on 2008-06-06
I am just tired of ten of the same questions always on the first page, geezer.  And I think it is far less hostile to tell them what they are doing wrong, rather than just mean-spiritedly ignoring their questions.  I was being kinder than you, you see? 

Besides, I am a Debian user, not an Ubongo user.  We are as mean as a crowd gets.  :p

Cup, the first thing you have to know is whether your driver is being loaded.

$ sudo -i
# dmesg |grep Wireless
(or WiFi)

If you see something like:
[  592.042394] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[  592.043435] iwl4965: Detected Intel Wireless WiFi Link 4965AGN REV=0x4

# ifconfig -a
You will see all the network interfaces recognized by your system.  These are set up in the /etc/network/interfaces file.  You can nano <filename> to edit, but you need to know your stuff first.  Try man interfaces.

I always set my LAN interfaces to manual settings, so they are always the same and I can name my computers.  Use 
$ kdesu kcontrol Internet&Network|NetworkSettings
... to set up your network interfaces.  Can't help you if yer using the hyper-simplefied Gnome.  If your interfaces are set to manual IP, you should see this IP when you # ifconfig.

Now the next step is to get associated with the AP.  When you iwconfig, it should show the ESSID and MAC of the AP, like this:
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Hex"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:21:a1:92
          Bit Rate=54 Mb/s   Tx-Power=14 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:D608-2AC7-22E4-0EB1-A0D5-DA13-BA86-AD75 [2]
          Link Quality=100/100  Signal level:-41 dBm  Noise level=-93 dBm

If not, ESSID will show none/any and MAC will be blank.

Beyond that, we need more detail on your particular symptom.
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Creap on 2008-07-12
Hi. I seem to having a similar problem.
> **Quantumstate said:**
> the first thing you have to know is whether your driver is being loaded.

$ sudo -i
# dmesg |grep Wireless
(or WiFi)

If you see something like:
[  592.042394] iwl4965: Copyright(c) 2003-2008 Intel Corporation
[  592.043435] iwl4965: Detected Intel Wireless WiFi Link 4965AGN REV=0x4

[   33.378775] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   33.378910] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
> **Quantumstate said:**
> 
# ifconfig -a
You will see all the network interfaces recognized by your system.  These are set up in the /etc/network/interfaces file.  You can nano <filename> to edit, but you need to know your stuff first.  Try man interfaces.


I have

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

Should I add an iface wlan0 inet dhcp ; auto wlan0 to this file?

> **Quantumstate said:**
> Now the next step is to get associated with the AP.  When you iwconfig, it should show the ESSID and MAC of the AP, like this:
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Hex"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:21:a1:92
          Bit Rate=54 Mb/s   Tx-Power=14 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:D608-2AC7-22E4-0EB1-A0D5-DA13-BA86-AD75 [2]
          Link Quality=100/100  Signal level:-41 dBm  Noise level=-93 dBm

If not, ESSID will show none/any and MAC will be blank.

Beyond that, we need more detail on your particular symptom.
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I simply get $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Any ideas? thanks.

---

### Post by Bobmatt on 2008-07-12
I am a complete Newbie with very little Linux experience, but i'm willing to learn, so be gentle with me. I have installed Ubuntu and have a similar problem with wireless on my Toshiba laptop. i have done the list from lshw and it doesn't show my wireless at all.

bob@bob-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1e:8c:e8:d2:93
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


Any help would be appreciated.

---

### Post by adldesigner on 2008-07-12
> **Bobmatt said:**
> 
       logical name: eth0

Bob, that line there tells you that your wireless interface is named **eth0**.
[COLOR=DarkOrange]**EDIT: No, it doesn't. Please read below for Edit Notes.**[/COLOR]

You can now try:
```
iwlist eth0 scan
```What you should look for in that output is an entry that says something in the lines of ESSID=your_networks_name.
If you see it, then that means that maybe you can connect to it.
So after that, you could try for:
```
sudo iwconfig eth0 essid your_networks_name
```And lastly:
```
dhclient eth0
```If this one outputs something like **bound to XXX.XXX.XXX.XXX** that means you that you should be connected to that wireless network.

This assuming that you don't have any encryption in place and that your router's giving out DHCPOFFERS, and that your Network Manager's (System > Network) connection settings for *your_network_name* is Automatic configuration (DHCP).

Hope this helps,
[B][COLOR=DarkOrange]
EDIT: I just noticed that you're actually saying that you're system is not recognizing your wireless card! Sorry mate. What I said still applies, provided that you can get the card working, and find out what your wireless interface is.[/COLOR][/B]

---

