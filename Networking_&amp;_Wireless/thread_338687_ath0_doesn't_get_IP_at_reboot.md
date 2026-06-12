---
title: "ath0 doesn't get IP at reboot"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by multiverse on 2007-01-14
I use Applications >> System >> Networking tool to manage my wireless connection (see attachment).  In a fit of obsessiveness I decided to harden my wireless router.  I believe the changes I made are highlighting a weakness of Xubuntu wireless or misconfiguration.  I have tested the changes against three systems:  Windows, OS X and Xubuntu, and Xubuntu is the only system that has problems with the changes.  The problem is that the wireless connection cannot obtain a lease from the wireless router's DHCP server at the time of boot:  I can, however, obtain a lease when I use the connection manager.  All three systems worked on the wireless router prior to the changes I made.  So let me tell you what I have and what I changed:

**NOTEBOOK**

Dell Inspiron 1000

**OS**

Xubuntu 6.10

**WIRELESS NIC**

Netgear WG511

**WIRELESS ACCESS POINT**

Linksys WRT54G with DD-WRT #22 (talismen)

**THE CHANGES ON THE WIRELESS ROUTER**

**1)  Setup >> Basic Setup**

Network Address
Server Settings (DHCP)
Starting IP Address: 	 192.168.1.2 [COLOR="Red"]<<-- This used to be 100[/COLOR]
Maximum Number of  DHCP Users: 10 [COLOR="Red"]<<-- This used to be 50 [/COLOR]

**2)  Wireless >> MAC Filter**

Wireless MAC Filter:  Enable
Permit only: 	  Permit only PCs listed to access the wireless network

Then I added the 5 MAC addresses I need to be white-listed

**3)  Administration >> Management >> Dhcp**

DHCP:  Enabled
Static Allocations:  I paired 8 valid IP Addresses with 8 valid MAC addresses (triple-checked for accuracy) (please view attachment for details)

**SUMMARY**

Xubuntu isn't picking up an IP address on reboot, but it does if I use the connection manager.  A review of the router proves there are no real problems with it's configuration.  The other systems in the house connect normally.

What could be wrong?

P.S.

Here is what it looks like before I get my lease

ath0      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:A0  
          inet6 addr: fXXX::2XX:bXXX:fXXX:9XXX/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2854 (2.7 KiB)  TX bytes:8977 (8.7 KiB)

---

### Post by maxamillion on 2007-01-14
```
sudo aptitude wifi-radar
```

Use that to manage wifi network connections. Wireless and printer config (along with other things like smb share browsing) are things that are being worked on improving under Xubuntu and hopefully will see a great improvement with the release of feisty.

---

### Post by multiverse on 2007-01-14
> **maxamillion said:**
> ```
sudo aptitude wifi-radar
```

Use that to manage wifi network connections. Wireless and printer config (along with other things like smb share browsing) are things that are being worked on improving under Xubuntu and hopefully will see a great improvement with the release of feisty.

I had wifi-radar installed already.  Editing the properties for the AP did not resolve the reboot problem.

---

### Post by multiverse on 2007-01-15
Obeying my primal instinct to change things during the course of the problem, I have made the following change.  I upgraded the router software to DD-WRT v23 SP2 (09/15/06) std.  The problem still exists.

---

### Post by multiverse on 2007-01-15
More information:

 /etc/network/interfaces

auto ath0
iface ath0 inet dhcp
wireless-essid multiverse

---

### Post by multiverse on 2007-01-15
bumping for the day crew

---

