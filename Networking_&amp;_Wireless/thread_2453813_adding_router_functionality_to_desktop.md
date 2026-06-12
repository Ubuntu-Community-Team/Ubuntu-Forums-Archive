---
title: "adding router functionality to desktop"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by sp40140 on 2020-11-17
Hello
Is it possible to make the ubuntu computer to network routing as well?
Essentially I want to remove the Wi-Fi router and replace it with wired router and access point.
I already have i5 running ubuntu. 
Is there a package (software) available such that I can dump routing responsibility on the computer?
I don't have two Ethernet ports but can purchase one and install it.
I also would like to run pihole (or some alternative).

I am looking to do this as I have about 70 devices on my network and off the shelf Wi-Fi routers don't have enough power. 
And the quality wired routers cost a lot. 
It makes lot of sense for me if I can convert the computer running ubuntu right now to do routing for me.
Ideally I'd like to ADD routing function to general purpose computer.

---

### Post by Tadaen_Sylvermane on 2020-11-17
[https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source](https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source)

I'd welcome testing by others on the above script I've been working on. I've got it working thus far in a KVM vm with KVM Xubuntu machine on an isolated network. You do need to install and configure your dhcp / dns though. I'm currently using dnsmasq.

---

### Post by sp40140 on 2020-11-17
Thank you for quick response.
That does look interesting.
However, I am looking for something production quality. highly stable. 
I could look into testing it but I'm not comfortable making this script my primary router. As the network uptime is quite a high priority for me right now.

---

### Post by Tadaen_Sylvermane on 2020-11-17
My script does nothing more than configure iptables which is where the magic happens. Production level open source routers include OPNSense, and PFSense. I'm assuming a straight iptables configuration would meet production level reliability but you should have a dedicated machine for it regardless of which path you choose.

---

### Post by TheFu on 2020-11-17
> **Tadaen_Sylvermane said:**
> My script does nothing more than configure iptables which is where the magic happens. Production level open source routers include OPNSense, and PFSense. I'm assuming a straight iptables configuration would meet production level reliability but you should have a dedicated machine for it regardless of which path you choose.

+1. I've used both pfSense and currently run OPNsense. There are routers for $130-ish that run either of those systems wth 4GB RAM, Intel NICs and fast 64-bit CPUs.  Check out pcengines. These things should run 10+ years and have OSes that are easily maintained. 

If you like, openwrt can be loaded on the same hardware. There are other linux-based router/firewall distros too. 

You can build your own router with ubuntu as the base, but from a practical security standpoint, this machine should not run other services and many of the default things installed should be removed to aid security.

---

### Post by sp40140 on 2020-11-18
Great. Thanks. I will try out dedicated OPNsense machine.

---

### Post by TheFu on 2020-11-18
> **sp40140 said:**
> Great. Thanks. I will try out dedicated OPNsense machine.

I bought a PCEngines machine about 5 yrs ago. I made the mistake of not also buying the storage to be used at the same time and tried to get one locally.  Seems there are different mSATA standards and I got the wrong one.  So, I got an mSATA-SATA enclosure and planned to use the SATA port in the APU2 ... only to find that the power connector was also non-standard. This was a $2 part, but custom.

For a client, I bought an APU2 from a reseller in my country. It was much more expensive than buying direct. If you've put together legos or a desktop PC, this is pretty easy to put together from parts.

In short, I wish I'd purchased everything at the start, in the same order.
[LIST]
[*]APU2 - I got the 4G model "just in case". Doubt I needed that.
[*]Case - the metal case is part of the cooling and directly touches the CPU with thermal compound.
[*]PSU - I've learned over the decades to buy the recommended PSU. Running a Raspberry Pi with a non-approved PSU will quickly teach this lesson
[*]mSATA that fits the slot AND is seen by the firmware/OS.
[/LIST]

There are newer versions today. The 4-port model look interesting.
Installing OPNSense on this is something typical end-users will struggle to complete.  There is no GPU, so all communications are over a serial port. You'll want a USB-to-Serial cable, most likely, though my first setup worked by using dd from my linux system.

If you don't want to buy parts and build a 12W router, you should probably look at Ubiquiti and Mikrotik routers.  Both have good reputations for keeping their firmware patched and for having all the features a small business needs.  Just be very certain to ensure you understand what the connections are on anything you buy.  I was looking at Mikrotik RBs a few days ago and found a number of 10/100 version still being sold and a Gbps that provided only 450 Mbps to the WAN. These were less than $70 models.  The most important thing with buying a vendor "packaged" HW+SW router is that they maintain the firmware and patch for security issues quickly.  Performance is secondary, IMHO.

---

