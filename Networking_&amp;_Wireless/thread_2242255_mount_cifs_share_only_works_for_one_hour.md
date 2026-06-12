---
title: "mount cifs share only works for one hour"
date: 2014-08-31
forum: Networking &amp; Wireless
---

### Post by puil on 2014-08-31
I have an Ubuntu server that runs plex media server.
All my media is on a NAS which is Windows.

This has worked perfectly for years and years.
Last week, I updated the Ubuntu server from 12.x to 14.04.1.  As soon as I did that, my share stopped working.
If I try and access the share (ls /mnt/video) it just hangs.
If I reboot the server, everything works perfectly, for approximately 1 hour.  Then the mount dies again. It's 100% repeatable and never works after an hour.  I also want to point out that the NAS is up does not go offline ever.  It is rock solid.

I've been at this for 3 days now and I can't figure out what's wrong.  This is what's in my fstab:
```
//deepthought/video$   /mnt/video      cifs    ro,_netdev,username=plex,password=plex,sec=ntlm     0      0
```

Again, this worked for years.  I don't even see an error message or any way to troubleshoot.  I even tried reinstalling cifs-utils.  Nothing has helped.
Any advice would be appreciated.

---

