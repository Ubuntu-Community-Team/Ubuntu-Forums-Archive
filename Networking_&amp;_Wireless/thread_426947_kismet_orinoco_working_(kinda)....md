---
title: "kismet orinoco working (kinda)..."
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by liquidgeforce on 2007-04-29
Hey all im kinda new to ubuntu but im lovin it so far. after ALOT of foolin around i got my orinoco card to work with kismet with the newest ubuntu version. i did it by downgrading the firmware of the card to 6.06. the things is it works great, but it turns off after it captures about 200 packets...whats my problem? thnx alot

---

### Post by liquidgeforce on 2007-04-29
anyone? i really wanna get this working

---

### Post by chili555 on 2007-04-29
How about letting us see:```
lsmod | grep orinoco
lsmod | grep prism
lsmod | grep hostap
```Thanks.

---

### Post by tturrisi on 2007-04-29
stock kernel orinoco drivers have not worked well (or at all) w/ kismet in a long time. See this:
[http://ubuntuforums.org/showthread.php?t=286621](http://ubuntuforums.org/showthread.php?t=286621)

---

### Post by liquidgeforce on 2007-04-30
ubuntu@ubuntu:~$ sudo lsmod | grep orinoco
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

thanks. i installed suse 10.2 dual boot and the card works fine there, doesnt shut down, but i really hate suse and wanna get it to work on ubuntu, thanks

---

### Post by wiz561 on 2008-06-17
Hi!

Just so you know, I have the same exact problem as you do.  I haven't had much time to take a look at it, but just thought you should know you're not alone. 

I've got it working great with previous versions of ubuntu, but hardy seems to stop kismet after a handful of packets.  If I find an answer, I'll repost here...

---

