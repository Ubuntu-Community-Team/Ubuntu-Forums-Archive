---
title: "All rsync Transfers Are Slow"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by TheSpeedoBeast on 2008-10-14
I have been fighting with this problem on and off for a few months now, but finally had to swallow my pride and ask for help :)

I am using a guest Ubuntu Virtualbox install (on a Vista host) to connect to my straight Ubuntu backup server.

When I use SFTP inside of the Ubuntu guest to transfer files, my transfer rates are reasonable (about 5 MB/sec). However, when I try to use rsync to connect to the backup server, my rates drop substantially (about 80 kB/sec). I have tried using rsync through ssh, through rsyncd, and through samba shares, but none of those methods improve my transfer speeds.

My backup server is an a7n8x Asus motherboard, and my Virtualbox computer is on a ga-965p-ds3 motherboard. Any help is extremely appreciated.

---

