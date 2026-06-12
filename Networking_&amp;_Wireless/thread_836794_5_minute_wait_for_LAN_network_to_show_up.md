---
title: "5 minute wait for LAN network to show up"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by CRISM on 2008-06-21
I have two computers connected via Ethernet. The older computer is 900 MHz 256 MB machine running Dapper Drake. The newer computer is an AMD dual core 2.6 GHz 1GB machine running Hardy Heron. I am able to share files over the network just fine. But after boot-up (of either machine), I have to wait about 5 minutes before I can see my LAN network and the shared folders. This seems to be a time-out issue of some sort.

Anyone know why the long delay? When I run Windows on the same two computers, the LAN network shows up immediately. Is this a DNS or ipv6 problem? I know that my router (Belkin 54g) does not support ipv6.

---

### Post by CRISM on 2008-06-29
I found a partial solution that seems to greatly help. In the smb.conf file, I disabled all items related to network printers. This change has decreased the time for the computer and shared folders to show up on the network to about 30 seconds. A tremendous improvement from before. I don't know why even 30 seconds is required, but I'm willing to live with this.

---

