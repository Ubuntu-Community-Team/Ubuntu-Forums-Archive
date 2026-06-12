---
title: "proftpd/samba: Low writespeeds over gigabit LAN"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by lasermonkey on 2008-10-02
Hi I'm running Ubuntu Server 8.04.1
I have a software RAID5 that I get about 75 MB/s write and 100 MB/s read speeds with internally.

If I connect to the my proftpd server from my windows computer I get about 60 MB/s read from it, but only about 20 MB/s write.

Over samba filesharing i get about 25 MB/s write and 35 MB/s read. 

It's over a local gigabit network.

I've tried some tweaks for both smb.conf and proftpd.conf that I found googling, but none of them have helped much.

I get more CPU usage at the server when writing than reading, naturally because of the parity having to be calculated for the software RAID5, but still I have about 50% cpu idle when writing over ftp.

Why do I get so much lower speeds when writing as opposed to reading, especially over ftp?

---

