---
title: "DHCP issues (With simplest ethernet/router configuration ever)"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by sikanrong on 2008-02-18
Hey all, this is not my first hair-pulling parade while installing ubuntu. I'd thought I'd seen it all, and Ive even managed to get through most of "it all" without having to actually post my OWN thread. Looks like the buck stops here. So I just got a totally VIA setup. Via everything: whole mobo and on-board perhipherals. I have the VT6103 chipset. Anyway - after fighting the glorious battles of "**Reconfigure xorg.conf so that your stupid flatscreen has the right sync rates**", and the greuling trenches of "**For some reason apt is timing out with http, so I have to switch to ftp-only**", and who could forget "**How the hell do I share an internet connection from OSX to ubuntu**" - I finally thought I was okay. Actually, I thought I was pimp-****! So I went and got some speakers, thinking "this is IT! The last thing I have to do to this ******* thing before I can just sit back and enjoy!" ...and then I powered it down to re-arrange some circuit-breakery, and powered it back up, and everything was fine, but NO INTERNET. As a matter of fact, I couldn't even ping my OSX box anymore, and I didn't know why. Thinking I had messed something up, I re-installed ubuntu from scratch, only to find that now it wouldn't even DHCP connect on the live cd (actually the text-based alternate ISO, I was using the network-autoconfiguration utility that you get during the install). Previously this had worked. Now I'm freaking out. What to do? Well, I found a really long ethernet cable and managed to wire the ubuntu box directly to the router. I'm in Spain. My router is a Xavi 7868r, which is basically an ASDL modem and router -in-one. The router IS acting as a normal router, all the other machines in my house (I think like 6 WINXP boxes and my mac) are on the 192.168.1.x subnet. Still can't connect to the internet. Ive tried EVERYTHING. I've statically set the IP, used DHCP, checked the cable, and NOTHING works. (plugged it into my mac and shut off the Mac wifi, and it got online just fine, got the IP assigned in a millesecoond) A single time, I actually got a DHCP offer (on the ubuntu box) and got an IP assigned correctly, but didn't get the internet. This has never happened since. PLEASE HELP!!!

Here's a butt-load of data, lspci, ifconfig, and dhclient results, as well as the ping results from the router (did I mention I can't ping the router?)

fraureiber@frau-buntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

fraureiber@frau-buntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:50:70:C4:2B:2D  
          inet6 addr: fe80::250:70ff:fec4:2b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:8159 (7.9 KiB)
          Interrupt:17 Base address:0xe400 

eth0:avah Link encap:Ethernet  HWaddr 00:50:70:C4:2B:2D  
          inet addr:169.254.5.10  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74860 (73.1 KiB)  TX bytes:74860 (73.1 KiB)
  
fraureiber@frau-buntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface




iface eth0 inet dhcp
address 192.168.1.40
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

fraureiber@frau-buntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.5.10 icmp_seq=2 Destination Host Unreachable
From 169.254.5.10 icmp_seq=3 Destination Host Unreachable
From 169.254.5.10 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3999ms
, pipe 3

fraureiber@frau-buntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:70:c4:2b:2d
Sending on   LPF/eth0/00:50:70:c4:2b:2d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

I'm on 7.04 also (realized I forgot to say that bit.) - so yeah; HELP!!

---

### Post by jhetrick62 on 2008-02-19
Dude,

In your ifconfig you have 2 definitions for eth0.  The first one had no inet address and the second one has 169.254.5.10.  Usually when you get an ip address of 169.254.x.x, it means that you have no cable connected to your system or your network is un-plugged somewhere!  The machine assigns itself an ip address beginning with those octets.

You will find that to be true on a windows PC also.  So maybe you blew your internet port on your motherboard.

If you have a spare card or a usb broadband connection, plug them in and see if this solves your issues.

Jeff

---

### Post by sikanrong on 2008-02-19
Jeff - you're the man for responding so fast - I should've updated the post earlier but I did figure it out

1) the two eth0 interfaces are because of avahi, so that is actually all normal - you're right (btw) about the one being unplugged

2) the problem was the NIC card is simply faulty, and the long-and-short of the whole thing is that the damn onboard one was disabled in the BIOS when I got it because the little bolivian man I bought it from was using a different NIC (because he knew it was busted) - AND DIDN'T TELL ME! So i just spent like 1 1/2 days just trying to figure out that the card itself does, indeed, have HW problems.


Thanks for the attempted help, in any case

---

