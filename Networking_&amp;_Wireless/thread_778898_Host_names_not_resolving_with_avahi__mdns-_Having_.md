---
title: "Host names not resolving with avahi / mdns- Having to use IP numbers"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by wallyworld on 2008-05-02
I did a fresh install of Hardy on 2 AMD based machines with Gigabyte ga-ma78gm-s2h motherboards which use RTL-8111C LAN chips.  I could not ping, ssh, traceroute, etc using hostnames.  Had to use IP numbers.  After MUCH searching these forums, found nothing about the issue.  Checked logs in /var/log/daemon.log and found the avahi daemon had no errors.  Long story short, I found that with this particular motherboard, multicast packets seem to be ignored.  So I did the following command to enable multicast reception:

sudo ifconfig eth0 allmulti

After that, I could ping my MacBook Pro via its hostname, I could ping the other ubuntu box by hostname, ssh worked, etc...  Any networking experts out there who could advise if this is a good fix or something that needs to be looked at during the startup process for ubuntu?  Didn't seem to be a problem for my old MSI K9N SLI Platinum motherboard.  That board has a Vitesse VC8601 chip for LAN.

---

