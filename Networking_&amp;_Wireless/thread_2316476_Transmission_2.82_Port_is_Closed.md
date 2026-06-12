---
title: "Transmission 2.82 Port is Closed"
date: 2016-03-08
forum: Networking &amp; Wireless
---

### Post by David_Partridge on 2016-03-08
I installed transmission 2.82 onto Ubuntu Server LTS 14.04.4 after a few problems.

But, whatever I do I get "Port is Closed" when I try to get it working.

I have tried both using uPnP and manually opening a port in the router (which is a BT HomeHub5 Fibre to the Cabinet).

CanYouSeeMe.org sees that the port in the router is open.

I tried to trace using Wireshark, but clearly don't know enough to interpret the capture (without uPnP) :/

If it's any help I have attached the capture file:
[ATTACH]267709[/ATTACH]

Dave

---

### Post by houstonbofh on 2016-03-08
It could be your ISP using active packet inspection shutting down bit torrent.  There is no way to test this internally, however.

---

