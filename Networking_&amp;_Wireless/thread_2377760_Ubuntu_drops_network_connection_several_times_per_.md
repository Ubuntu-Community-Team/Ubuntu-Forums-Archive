---
title: "Ubuntu drops network connection several times per month"
date: 2017-11-16
forum: Networking &amp; Wireless
---

### Post by mbcl4848 on 2017-11-16
Hi all,

I have a server that is running Ubuntu command line only.  It is hosting samba and apache2 services, and I use it to record video by way of a capture card.  The problem is that the network interface (Ethernet) will repeatedly drop connection, and since I'm running it headless I have to reboot it in order to restore the networking.  I know that it is merely the networking interface going down because a) I still have recorded video from the period of time where the interface was down, and b) I set up a cron job once per minute to ping out, and I record this in a log so that I can see exactly when the disconnect occurs.  So far as I know the rest of the machine works fine even when the pings fail.

When the disconnect occurs, I get this in syslog:
```
Nov 14 09:56:39 linux-encoder avahi-daemon[899]: Withdrawing address record for w.x.y.z on enp1s0.
Nov 14 09:56:39 linux-encoder avahi-daemon[899]: Leaving mDNS multicast group on interface enp1s0.IPv4 with address w.x.y.z.
Nov 14 09:56:39 linux-encoder avahi-daemon[899]: Interface enp1s0.IPv4 no longer relevant for mDNS.
Nov 14 09:56:39 linux-encoder whoopsie[995]: [09:56:39] Cannot reach: https://daisy.ubuntu.com
Nov 14 09:56:39 linux-encoder whoopsie[995]: [09:56:39] offline
```

For several months it went several weeks between disconnects, and I never found a good pattern.  But the last two drops have been EXACTLY (like, to the minute) 8 days between drops.  I thought at first it was something weird with DHCP, but it does not appear that the DHCP leases coincide with the disconnects.

Any ideas?  Thanks in advance!

---

### Post by mbcl4848 on 2017-12-01
bump :D

It happened again, and again it was eight days to the minute.  Any ideas?

---

