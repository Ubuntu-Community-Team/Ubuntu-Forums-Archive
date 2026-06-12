---
title: "Eth0 Disconnected Issue."
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by CherenkovBlue on 2007-03-20
Hi. I just installed ubuntu 6.10 on my laptop (compaq presario v2000z) my NIC doesnt seem to be working correctly. i've been looking through these forums for hours trying to find a solution to my problem and so far nothing has worked.  when i first installed ubuntu it  gave me the error "SIOCGIFFLAGS error: No such device. After a bunch of mucking around in the terminal following the assistance given to other people with similar problems it now just says "status: disconnected" under eth0.

any help would be much appreciated.

---

### Post by Mr. C. on 2007-03-20
How many NICs does the system have?

Show output from the following commands:

```
sudo ifconfig -a
sudo lspci
sudo lspci -n
sudo grep eth0 /var/log/syslog

```
MrC

---

### Post by CherenkovBlue on 2007-03-20
[IMG]http://i7.photobucket.com/albums/y300/FeNiX117/000_07531.gif[/IMG]

[IMG]http://i7.photobucket.com/albums/y300/FeNiX117/000_07561.gif[/IMG]

[IMG]http://i7.photobucket.com/albums/y300/FeNiX117/000_07571.gif[/IMG]

[IMG]http://i7.photobucket.com/albums/y300/FeNiX117/ssd.gif[/IMG]




if you cant read those try these links:
[http://i7.photobucket.com/albums/y300/FeNiX117/000_07531.gif](http://i7.photobucket.com/albums/y300/FeNiX117/000_07531.gif)
[http://i7.photobucket.com/albums/y300/FeNiX117/000_07561.gif](http://i7.photobucket.com/albums/y300/FeNiX117/000_07561.gif)
[http://i7.photobucket.com/albums/y300/FeNiX117/000_07571.gif](http://i7.photobucket.com/albums/y300/FeNiX117/000_07571.gif)
[http://i7.photobucket.com/albums/y300/FeNiX117/ssd.gif](http://i7.photobucket.com/albums/y300/FeNiX117/ssd.gif)

sorry about the quality, its the best i could do at the moment.

---

### Post by CherenkovBlue on 2007-03-20
oh, i have two NICs, ones wireless.

---

### Post by Mr. C. on 2007-03-20
Ok, follow my post here:

[http://ubuntuforums.org/showthread.php?t=389260&highlight=mrc+disable](http://ubuntuforums.org/showthread.php?t=389260&highlight=mrc+disable)

MrC

---

### Post by CherenkovBlue on 2007-03-20
Thank you much.

---

