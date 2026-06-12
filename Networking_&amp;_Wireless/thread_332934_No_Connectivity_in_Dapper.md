---
title: "No Connectivity in Dapper"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by canucklehead on 2007-01-06
Hi guys. I've been using Ubuntu for about 6 months now and I've had no problems. However, I purchased a new desktop and set it up to dual boot WinXP SP2 and Ubuntu 6.06 and immediately encountered a problem: **I have absolutely no network connectivity when booting in Dapper.**

I'm a noob but I'll try and give you as much info as I can...

- I am on an ADSL line behind a Linksys WRT54G. I have a hardwired ethernet connection.
- I am using the onboard network adapter on my eVGA nForce 680i mobo.
- I have full local and Internet connectivity when using my Dapper LiveCD.
- I have full local and Internet connectivity when booting in Windows.
- When I run netstat -nr my routing tables are empty :-?
- When I run dhclient I get "No DHCPOFFERS received"
- I can ping localhost (127.0.0.1) but not my router.

Any ideas? Thanks a bunch.

---

### Post by teaker1s on 2007-01-06
it's not something as simple as ethernet isn't activated?
on gnome panel
system-administration-networking

if after this you can get to router but not internet, in networking set static ip and manually enter your isp DNS server address

---

### Post by canucklehead on 2007-01-06
eth0 and eth1 are activated. I can't ping the router.

---

