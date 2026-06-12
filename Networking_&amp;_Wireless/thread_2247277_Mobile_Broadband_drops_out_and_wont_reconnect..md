---
title: "Mobile Broadband drops out and wont reconnect."
date: 2014-10-06
forum: Networking &amp; Wireless
---

### Post by kazakore on 2014-10-06
I have a Lenovo X230 laptop running Ubuntu Studio 14.04 (so XFCE based) with built in mobile broadband, which takes a simcard inserted underneath the battery. Generally it appears to work fine for some time but then it will just drop out and no matter what I try I can not get it to reconnect without restarting the laptop!

lsusb shows this line:
Bus 003 Device 002: ID 0bdb:1926 Ericsson Business Mobile Networks BV

Sure I have found more useful information at some point in the past but can't remember how... Couldn't see anything in sudo lshw


Generally it currently seems to be working fine for some time (and generally doesn't drop out if I have a solid connection just as running an update or wgetting a file. Uploading images to my Facebook account doesn't keep it open though!) but then will suddenly claim it has 0% connectivity, whereas it normally states 80% when working in my current location, and attempting to reconnect and it just refuses.

I have tried running sudo restart network-manager which I'm sure has helped with similar type problems before but does nothing with this.


Anything else I can try? Any more information I can give you to help me?

---

### Post by mcparty2 on 2014-10-07
A few thoughts, it may be able to help: 

1, Does it drop randomly? Maybe it could be due to a preiod of in activity causing the network to cut off in which case check your power settings. To test this, try running a continuous ping to google's dns server 8.8.8.8 to see if it drops, if it doesn't drop it is not likely to be a power setting timeout issue.

2, "simcard inserted underneath the battery" - Not the most sensible  place to place a sim card as the signal would be suseptible to  electronic interference which may be produced by faulty electrical  equipment which may explain the sudden drops. 

3, Are there any errors in /var/log/syslog at the time the drops occur?

I hope this helps?

---

### Post by kazakore on 2014-10-07
> **mcparty2 said:**
> 
1, Does it drop randomly? Maybe it could be due to a preiod of in activity causing the network to cut off in which case check your power settings. To test this, try running a continuous ping to google's dns server 8.8.8.8 to see if it drops, if it doesn't drop it is not likely to be a power setting timeout issue.

That sounds feasible. Although it is at random times it doesn't usually take too long (ie less than a few hours) yet it managed to download updates over a few hours without disconnecting (internet is VERY slow out here!) and does appear to remain connected if there is something currently downloading most of the time.

Not any settings in the Settings Manager and pretty sure I have previously set any power saving options for both USB and PCI to Off within BIOS, to make sure audio interfaces work correctly. Could be a hang-over from the Windows install it came with and UEFI though. As, for example, setting the default screen brightness up in Windows affects all other OSes, including those you boot from a USB drive!.... Haven't quite got around to fully removing Windows (was actually going to today, almost did yesterday) so maybe I should look there first...

PS. for an idea how bad the connection is!

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=44 time=1708 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=44 time=1045 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=44 time=2468 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=44 time=1587 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=44 time=1067 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=44 time=1866 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=44 time=2126 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=44 time=1163 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=44 time=823 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=44 time=2824 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=44 time=2345 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=44 time=3865 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=44 time=3045 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=44 time=2644 ms
64 bytes from 8.8.8.8: icmp_seq=15 ttl=44 time=2425 ms
64 bytes from 8.8.8.8: icmp_seq=16 ttl=44 time=3123 ms
64 bytes from 8.8.8.8: icmp_seq=17 ttl=44 time=3264 ms
64 bytes from 8.8.8.8: icmp_seq=18 ttl=44 time=3244 ms
64 bytes from 8.8.8.8: icmp_seq=19 ttl=44 time=2821 ms
64 bytes from 8.8.8.8: icmp_seq=20 ttl=44 time=2642 ms
64 bytes from 8.8.8.8: icmp_seq=21 ttl=44 time=3243 ms
64 bytes from 8.8.8.8: icmp_seq=22 ttl=44 time=2882 ms
64 bytes from 8.8.8.8: icmp_seq=23 ttl=44 time=2762 ms
64 bytes from 8.8.8.8: icmp_seq=24 ttl=44 time=5621 ms

---

### Post by tgalati4 on 2014-10-07
Is your battery swollen?  It doesn't take much pressure on a simcard to lose contact.  I've seen MacBook batteries swell such that they cause the touchpad to stop working.

---

### Post by kazakore on 2014-10-08
Battery not swollen and if it was not sure it would affect it as placement is more under the connection area, not the main part of the battery. Although, as an experiment I had tried removing the battery and simcard and reinserting and this also allowed me to reconnect.

But some kind of power saving or similar feature seems most likely as it has been up and running a good few hours now with a "ping -i 8 www.google.com" running to keep it connected. Even if my average time is something around 15 seconds (with worst I've seen of 40 seconds!) :o

---

