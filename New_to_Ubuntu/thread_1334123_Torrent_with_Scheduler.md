---
title: "Torrent with Scheduler"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by TironN on 2009-11-22
Hey ladies and gents,
Is there any (good) torrent program with the ability for scheduling? I really need to cut back on peak downloads and back in my windows days i used utorrent and used the scheduler to allow it to work only 2am-12pm.
So is there a linux alternative?

---

### Post by nadian on 2009-11-22
kttorent with scheduler plugin activated in settings - its in synaptic package manager

---

### Post by TironN on 2009-11-22
Excellent! That seems to be working fine. Now to wait until tomorrow morning to see if it worked!

---

### Post by 3rdalbum on 2009-11-22
You don't seem to have looked very hard for a torrent client that can do scheduling... Transmission is in the stock Ubuntu install and it can change its bandwidth usage depending on the time. I've been using it for the last few days. Before they added this feature, I just used transmission-remote and my crontab to change the bandwidth depending on time as well.

---

### Post by frenchn00b on 2009-11-22
> **TironN said:**
> Hey ladies and gents,
Is there any (good) torrent program with the ability for scheduling? I really need to cut back on peak downloads and back in my windows days i used utorrent and used the scheduler to allow it to work only 2am-12pm.
So is there a linux alternative?

 crontab -e
```
# m h  dom mon dow   command
0 12 * * *     screen -d -m  rtorrent
```

---

