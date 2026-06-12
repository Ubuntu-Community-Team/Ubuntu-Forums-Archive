---
title: "Connecting to the internet (noob question)"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by halkonst on 2007-02-18
I just installed Ubuntu Edgy Desktop for AMD64 on my machine but I can't get a working internet connection. I have two network cards, on integrated in my motherboard (eth0) which I intend to use for LAN, and one regular PCI from RealTek that I plugged my internet cable into. I don't know the full names for any of them but both have worked in Linux previously (Debian, maybe 1-2 years ago). I connect a network cable from the RealTek port directly to my ADSL-modem, no routers or hubs between, and I type in exactly the same information in my interfaces- and resolve.conf-files that work under windows. My problem is that I can't connect to anything at all. I can't even ping my gateway. I don't know what the cause is and I need help. If you have an idea what might be wrong please answer. Thanks for your time. Relevant information included below.

EDIT: To clarify, my ISP doesn't use PPPoE, they do it strayt ethernet. I don't have any username or password for my internet connection. The ppp stuff in my interfaces file is only there cause I decided to run pppoeconf when I was running out of **** to try...

[QUOTE="interfaces"]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (INTERNET)
auto eth1
iface eth1 inet static
          address xxx.xxx.xxx.238
          netmask 255.255.255.0
          network xxx.xxx.xxx.0
          broadcast xxx.xxx.xxx.255
          gateway xxx.xxx.xxx.1
          # dns-* options are implemented by the resolvconf package, if installed
          dns-nameservers xxx.xxx.228.3 xxx.xxx.227.3

# The secondary network interface (LAN)
auto eth0
iface eth0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider
[/QUOTE]

[QUOTE="resolv.conf"]
nameserver xxx.xxx.228.3
nameserver xxx.xxx.227.3
[/QUOTE]

[QUOTE="ifconfig output for eth1"]
eth1        Link encap:Ethernet    HWaddr 00:30:4F:1C:E0:64
              inet addr:xxx.xxx.xxx.238    Bcast:xxx.xxx.xxx.255    Mask:255.255.255.0
              inet6 addr: fe80::230:4fff:felc:e064/64    Scope:Link
              UP BROADCAST MULTICAST    MTU:1500    Metric:1
              RX packets:9 errors:0 dropped:0 overruns:0 frame:0
              TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:540 (540.0 b)    TX bytes:155724 (152.0 KiB)
[/QUOTE]

---

### Post by lloyd_b on 2007-02-19
First off - are you sure that the Realtek is at eth1 and the onboard ethernet is at eth0?  You mention that you "intend to use eth0 for the lan", but don't specify whether or not it's actually connected at this point.  

Easy enough to test - move the cable from the RealTek port to the onboard port and see what happens.

If that doesn't help, could you provide a bit more info regarding the ethernet devices?  Specifically, in a terminal window run the "lshw" command, and post any results that seem to refer to an ethernet device.

Also, could you provide the output from running the "route" command?  It looks like you've got the gateway and network properly defined, but it never hurts to double check these things.

Finally, as a test (once you've verified which port is eth0 and which is eth1) try reconfiguring eth0 to those settings, and connecting it to the modem, and see if it works.

A comment - I've seen a fair number of problems here on the boards regarding weird issued with certain RealTek cards.  This could be another instance of the same (or not - it depends on the specific card involved).

Lloyd B.

---

### Post by halkonst on 2007-02-19
Yes, the Realtek is at eth1, I made sure of this by looking in the Device Manager and toying with ifup/ifdown while eth1 was connected to my other computer. I'm gonna give you some hardware info. Full name of the Realtek is RTL-8139 and at the info.linux.driver key it says 8139too. Full name of the integrated ethernet device is 88E8001 Gigabit Ethernet Controller from Marvell Technology Group, the info.linux.driver says skge and it's at interface eth0. The eth0 is not connected at this point. The only network cable connected to the computer is the one from the modem to the Realtek card at eth1.

I've tried moving things around like you suggested. I've tried changing between ethernet ports both with and without changing in my /etc/network/interfaces. Nothing works. I can't connect to anything no matter what settings I use or which port I use.

I ran those commands you asked me to. Check below. Thank you for your help.

[QUOTE="lshw"]
...
*-network:0
description: Ethernet interface
product: 88E8001 Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: a
bus info: pci@00:0a.0
logical name: eth0
version: 13
serial: 00:0e:a6:90:f5:5a
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock 66MHz
capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd
100bt 100bt-fd 1000bt 1000bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=skge driverv
ersion=1.5 duplex=full firmware=N/A link=no multicast=yes port=twis
ted pair speed=100MB/s
resources: iomemory:fdd00000-fdd03fff ioport:ec00-ecff irq:193

*-network:1
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: b
bus info: pci@00:0b.0
logical name: eth1
version: 10
serial: 00:30:4f:1c:e0:64
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd
100bt 100bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=8139too driv
erversion=0.9.27 duplex=full ip=xxx.xxx.xxx.238 link=yes multicast=yes 
port=MII speed=100MB/s
resources: ioport:e800-e807 ioport:e400-e403 ioport:e000-e007 ioport:
d800-d803 ioport:d400-d40f ioport:d000-d0ff irq:177
...
[/QUOTE]

[QUOTE="route"]
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
localnet * 255.255.255.0 U 0 0 0 eth1
default xxx.xxx.xxx.1 0.0.0.0 UG 0 0 0 eth1
[/QUOTE]

---

### Post by halkonst on 2007-02-19
I'm really stumped for things to try here, and it's such a weird problem I can't figure out what might cause it. I've been searching for solutions online and I found a few suggestion, none of them worked. I tried booting with noapci, I tried reinstalling, I tried modprobing a bunch of different drivers but it just won't work. What can I do? Having an internet connection is kind of important to me, and going back to Vista is not an option. I need this to work. Might another release of ubuntu work better? Or another Linux distro like Debian (was kind of set on ubuntu tho...). Please help me.

---

### Post by Sarteck on 2007-02-19
I'm experiencing a very similar problem, and with the same RealTek, as well.

If I find a solution, I'll post it, or if you find it before me, could you post it? XD

---

### Post by Sarteck on 2007-02-19
Huh, whaddya know?  For me, it WAS switching **eth0** with **eth1** that worked.  Odd, though, because previous OSes on here recognized it the other way around.

However, now I have another problem...  When I try to access a site by name instead of IP address, it won't let me.

In my Network configuration thingie, there is no option for setting a primary DNS thingamabobber, and I'm guessing that's the problem.  Can anyone help?

---

### Post by halkonst on 2007-02-19
What do you mean when you say you switched eth0 and eth1? Switched how? I just installed Dapper 32bit instead of the Edgy 64bit I had previously but I still have the same problem... Damn.

As for the DNS stuff, you can edit that in the DNS tab in System > Administration > Networking, or by typing sudo nano /etc/resolv.conf and edit it manually (don't forget to edit the same stuff in /etc/network/interfaces too). I hear these DNS-servers are kinda good: [http://www.opendns.com/start/](http://www.opendns.com/start/)

---

### Post by lloyd_b on 2007-02-19
> I'm really stumped for things to try here, and it's such a weird problem I can't figure out what might cause it. I've been searching for solutions online and I found a few suggestion, none of them worked. I tried booting with noapci, I tried reinstalling, I tried modprobing a bunch of different drivers but it just won't work. What can I do? Having an internet connection is kind of important to me, and going back to Vista is not an option. I need this to work. Might another release of ubuntu work better? Or another Linux distro like Debian (was kind of set on ubuntu tho...). Please help me.

I really don't see anything wrong in the info you've posted.  Everything looks like it *should* be working (but obviously isn't).

The RTL8139 is one of the cards I've seen having problems, but that doesn't explain why you can't connect with the onboard ethernet.

FYI - in one previous case, the person was able to get the card to work with SuSe Linux.  From that, we decided that it's something to do with the kernel version/driver version.  You could try loading Dapper rather than Edgy, and see if that makes a difference.

Lloyd B.

---

### Post by halkonst on 2007-02-19
I just did load in Dapper 32bit, instead of the Edgy 64bit I had at first, but the problem remains. This is just so strange.

---

### Post by halkonst on 2007-02-19
I don't know if this information helps but I just tried setting up a LAN with my windows computer and I had the same problems there as I have with the internet connection. I set up the network with static IP's on both sides and tried pinging. The windows comp could ping the ubuntu comp fine but on the ubuntu side it looked the same as when I try to ping the gateway for my internet connection; nothing happend. Ubuntu was connected to the LAN, and it did respond to ping, but it can't send a ping of it's own. What does this mean? And what do I do to fix it??

---

### Post by lloyd_b on 2007-02-20
>  I don't know if this information helps but I just tried setting up a LAN with my windows computer and I had the same problems there as I have with the internet connection. I set up the network with static IP's on both sides and tried pinging. The windows comp could ping the ubuntu comp fine but on the ubuntu side it looked the same as when I try to ping the gateway for my internet connection; nothing happend. Ubuntu was connected to the LAN, and it did respond to ping, but it can't send a ping of it's own. What does this mean? And what do I do to fix it??

Question: When you ping a host from a terminal window, what message (if any) do you see?  "Destination Host Unreachable"? "Network Unreachable"?

The situation you describe is really weird.  If the Windows machine is getting responses to it's pings, then the ethernet driver is working, and Ubuntu's TCP stack is working as well.  But you can't ping out.

What you may be looking at is a compatibility issue with the 64bit motherboard.  In which case switching to a more recent kernel may take care of things.  But I'm just making guesses at this point.

Hopefully somebody else will wander by with a suggestion...

Lloyd B.

---

### Post by halkonst on 2007-02-20
Good news, the **** works! I don't understand why but it does. Late last night I changed my DNS servers from the ones supplied by my ISP to the ones available from opendns.com. I never tried if it worked then but when I woke up today and turned on the computer, I had internet. YEA!! It's still all very weird, but atleast now it works. Thanks for all your help lloyd

---

