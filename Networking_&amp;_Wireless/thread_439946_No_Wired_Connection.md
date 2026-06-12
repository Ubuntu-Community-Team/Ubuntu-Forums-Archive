---
title: "No Wired Connection"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by TheoMurpse on 2007-05-11
I am plugged into my router, and when I turn on my computer and boot up, I have an IP (192.168.1.103). I have in Network Settings my wired connection configured for DHCP.

However, I cannot ping anything, and have no apparent connection to even my router. My router does not list this computer in the DHCP Clients table (DD-WRT on the router). "ifconfig eth0" gives the expected information: IP is 192.168.1.104, no Gateway is listed, Bcast is 192.168.1.255, and netmask is 255.255.255.0.

ifconfig eth0:
Link encap:Ethernet HWaddr 00:40:45:19:18:18
inet addr:192.168.1.104 Bcast 192.168.1.255 Mask:255.255.255.0
inet6a addr: blahblah Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets 4 errors:0 dropped:0 overruns:0 frame:0
TX: 2   0 0 0 0
collisions:0 txqueuelen:1000
RX bytes 1300 (1.2 KiB) TX bytes:684 (684.0 b)
Interrupt:11 Base address:0xd800

Why does my router not list me, and why do I not get a connection? I have no problems when I do this via Windows XP with the same computer, and I've had no problems with this with Windows XP on other networks (this is a laptop computer).

---

### Post by lloyd_b on 2007-05-11
Your "ifconfig" output looks perfectly normal.

Could you post the following info:

1.  The output from running the "route -n" command in a terminal window.
2.  The *contents* of the file "/etc/resolv.conf"
3.  The *contents* of the file "/etc/network/interfaces"

And some experiments.  In a terminal window:

1.  "ping -c 1 192.168.1.1"  (I *suspect* this is your gateway's IP address).
2.  "ping -c 1 72.14.253.99" (This is one of Google's IP addresses)
3.  "nslookup www.google.com" (To see if you have DNS working).

You are getting an IP address from somewhere.  Either your machine is getting if via DHCP, or it's statically configured ("/etc/network/interfaces" will tell us which).

I'm *guessing* that you're getting your configuration via DHCP, but that it's not giving you good DNS info, so it's having problems looking up names.  The experiments above will nail down whether or not this guess is correct.

Lloyd B.

---

### Post by DWRZ on 2007-05-11
I'm having a similar (same?) issue, check out my thread: [http://ubuntuforums.org/showthread.php?t=437687](http://ubuntuforums.org/showthread.php?t=437687) and, well, good luck. :(

---

### Post by TheoMurpse on 2007-05-19
> **lloyd_b said:**
> Your "ifconfig" output looks perfectly normal.

Could you post the following info:

1.  The output from running the "route -n" command in a terminal window.
2.  The *contents* of the file "/etc/resolv.conf"
3.  The *contents* of the file "/etc/network/interfaces"

And some experiments.  In a terminal window:

1.  "ping -c 1 192.168.1.1"  (I *suspect* this is your gateway's IP address).
2.  "ping -c 1 72.14.253.99" (This is one of Google's IP addresses)
3.  "nslookup www.google.com" (To see if you have DNS working).

You are getting an IP address from somewhere.  Either your machine is getting if via DHCP, or it's statically configured ("/etc/network/interfaces" will tell us which).

I'm *guessing* that you're getting your configuration via DHCP, but that it's not giving you good DNS info, so it's having problems looking up names.  The experiments above will nail down whether or not this guess is correct.

Lloyd B.

Here are my results (today my laptop's "acquired" IP is 192.168.1.104):
1.
Kernel IP routing table
Destination     Gateway          Genmask          Flags Metric Ref Use Iface
192.168.1.0     0.0.0.0            255.255.255.0   U    0       0 0 eth0
169.254.0.0     0.0.0.0            255.255.0.0       U    1000 0 0 eth0
0.0.0.0             192.168.1.1     0.0.0.0              UG  0       0 0 eth0

2.
cat /etc/resolv.conf
search austin.rr.com
nameserver 24.93.41.125
nameserver 24.93.41.126

3.
cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid philipjfry
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

auto ra0

Now for the experiments:
1.  "ping -c 1 192.168.1.1"  (this is my gateway).
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.104 icmp_seq=1 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


2.  "ping -c 1 72.14.253.99" (This is one of Google's IP addresses)
PING 72.14.253.99 (72.14.253.99) 56(84) bytes of data.
From 192.168.1.104 icmp_seq=1 Destination Host Unreachable

--- 72.14.253.99 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

3.  "nslookup www.google.com" (To see if you have DNS working).
;; connection timed out; no servers could be reached

---

### Post by lloyd_b on 2007-05-20
> Now for the experiments:
1. "ping -c 1 192.168.1.1" (this is my gateway).
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.104 icmp_seq=1 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms 

My guess was dead wrong.  Your problem is with the "first step" - between the computer and the router, not with DNS...

This makes no sense.  Normally I'd suspect a bad network cable or something of the sort, but  that's obviously impossible in this case - if there was a problem with the network cable, you wouldn't be receiving the DHCP configuration info.

All of the info you posted looks normal - IP address, routes, nameservers, etc.

So the DHCP client is able to use the network connection to get the configuration info, but after that, it acts like it isn't connected to the router.....

Do you have any sort of firewall installed on the machine?  A misconfigured firewall could potentially cause issues like this.

Other than that, I haven't a clue.  Hopefully somebody else will chime in with a suggestion.

Lloyd B.

---

### Post by thehuman on 2007-05-20
Has anyone figured this out? I am having the same problem--wireless works fine, but no wired connection. Not a MAJOR issue for me, but it is a little annoying knowing that something doesn't work. There seems to be a lot of threads on this same topic.

---

### Post by TheoMurpse on 2007-06-01
I installed Xubuntu and it works fine now. Thanks anyways anyone who came here.

---

