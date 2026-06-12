---
title: "Public IP on Ubuntu guest running in virtualbox running in Ubuntu 12.10"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by rss181919 on 2013-10-05
I have AT&T UVerse as my ISP.  About 6 months ago I purchased 4 public IP's from them just to play around with.

They had me setup my NVG510 router/gateway as follows:
Private LAN Subnet
Device IPv4 Address=192.168.1.254     
Subnet Mask=255.255.255.0     
DHCPv4 Start Address=192.168.1.64
DHCPv4 End Address=192.168.1.84

Public Subnet
Public Subnet Enable=ON        
Public IPv4 Address=107.220.46.254
Public Subnet Mask=255.255.255.248    
DHCPv4 Start Address=107.220.46.249    
DHCPv4 End Address=107.220.46.253

I have several physical machines attached to the LAN running different OS's and all using DHCP.
I have a few linux machines and a few windows machines.
One of my linux machines is a server.  It is setup as follows:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Inside this linux machine, I have virtualbox 4.2.12 installed.
Within this virtualbox, I have a couple of windows xp machines
to which I assigned my public IP's.  And example setup is as follows:
ip=107.220.46.252
subnet=255.255.255.248
gateway=107.220.46.254

and i have preferred dns defined also.

This has worked fine for the xp public server guests.

Now I want to setup an ubuntu public server quest in my virtualbox.
However, I can't figure out how to setup the networking on the guest to get that accomplished.
And although xp seems to work fine with the host ubuntu 12.10 server being setup as a dhcp but I am beginning to think that
the ubuntu guest might require me to change the ubuntu host network setup before it will work.

By the way, the ubuntu host and guest are 64 bit and the host is 12.10 and the guest is 12.04.
Any help is much appreciated.

---

### Post by rss181919 on 2013-10-07
I figured out my problem.   I needed a bridge on the host.  I then had to point virtualbox guest setup to that bridge.  I was then able to setup the guest interfaces file with my public static ip information.:D

---

