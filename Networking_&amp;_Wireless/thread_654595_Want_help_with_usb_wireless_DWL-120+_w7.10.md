---
title: "Want help with usb wireless DWL-120+ w/7.10"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by chapmc on 2007-12-31
I would like someone to help me get my usb wireless device (d-link DWL-120+) to work with ubuntu 7.10.  I am not in any hurry because this is on a extra computer I have.  I want to take my time and let someone guide me through the process and maybe a windows user will learn some things about ubuntu.  

Here is the situation if you are interested.

I had ubuntu 6.06 running on this machine and it was working fine.  Where the machine was located, the wireless connection was all I had.  I had previously tried installing 6.10 but lost the wireless support so went back to 6.06.  I decided I would try to upgrade to the latest version.  I upgraded to 6.10 but couldn't go beyond that because the update manager didn't work (I don't remember the exact reason).  So I installed 7.10 using the alternate CD.  The wireless device does not work with this release.  I currently have moved the machine where I can use ethernet connection as well as wireless.

I booted from the 6.06 live CD and the wireless works with it.  Here is /etc/network/interfaces.

chap@ubuntu:~$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp

iface eth0 inet dhcp
auto eth0
______________________
The network manager shows "wired connection" for both wlan0 and eth0.
---------------------------------------------------------------
Here is the output from a ping to my router.  I don't know why the IP address shows different.

chap@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 169.254.8.148 icmp_seq=1 Destination Host Unreachable
From 169.254.8.148 icmp_seq=2 Destination Host Unreachable
From 169.254.8.148 icmp_seq=3 Destination Host Unreachable
From 169.254.8.148 icmp_seq=4 Destination Host Unreachable
From 169.254.8.148 icmp_seq=5 Destination Host Unreachable
From 169.254.8.148 icmp_seq=6 Destination Host Unreachable
From 169.254.8.148 icmp_seq=7 Destination Host Unreachable
From 169.254.8.148 icmp_seq=8 Destination Host Unreachable
From 169.254.8.148 icmp_seq=9 Destination Host Unreachable
From 169.254.8.148 icmp_seq=10 Destination Host Unreachable
From 169.254.8.148 icmp_seq=11 Destination Host Unreachable
From 169.254.8.148 icmp_seq=12 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
13 packets transmitted, 0 received, +12 errors, 100% packet loss, time 12033ms
, pipe 3
chap@ubuntu:~$ 
---------------------------------------
chap@ubuntu:~$ lsusb
Bus 001 Device 004: ID 2001:3b00 D-Link Corp. [hex] 
Bus 001 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
chap@ubuntu:~$ 
------------------------------------------------------

I did a search on dwl-120+ chipset and found a document saying that the driver sb acx100-usb.
-------------------------------------------------

If you are willing to give me direction I will appreciate.  
And Happy New Year.

---

