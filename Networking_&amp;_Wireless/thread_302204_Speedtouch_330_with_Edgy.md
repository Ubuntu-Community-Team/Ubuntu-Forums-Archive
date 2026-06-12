---
title: "Speedtouch 330 with Edgy"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by lwr on 2006-11-18
Hi, I know there's a thread already similar to this, but I think I'm getting different errors.
Anyway, I've previously used [this guide]("http://www.ubuntuforums.org/showthread.php?t=128875") to get it working, modifying things as I described on page 3 to get it working on Dapper. However, doing the same thing on Edgy, I've been unable to connect. When I do pppd call adslscript, it tells me it's loaded, but I have no connection. Any ideas what could be wrong. I'm willing to try another method provided it's pretty simple.

Thanks for your help.

Luke

---

### Post by lixy on 2006-11-18
Though I didn't try it on Edgy, I'm pretty confident that this [script]("http://steve-parker.org/speedtouchconf") works virtually anywhere. Oh, and very easy to use :-D

---

### Post by galvatron1983 on 2006-11-18
Ugh the Speedtouch 330, probably the most annoying modem ever created, thank god for my router!

---

### Post by lixy on 2006-11-18
> **galvatron1983 said:**
> Ugh the Speedtouch 330, probably the most annoying modem ever created, thank god for my router!

I got it up and running within moments 4 years ago thanks to Mr. Parker's script. But I guess in this day and age, we're expecting out-of-the-box support for everything. Damn you Ubuntu for creating a generation of spoiled linuxians!!! :mrgreen:

---

### Post by lwr on 2006-11-18
Thanks for your suggestion lixy. Unfortunately, that script doesn't work on Edgy because the kernel version's too new. I've since played about with many different tutorials, I even installed Hoary on one machine to see if I could get that working, but sadly to no avail. Then I realised I've been putting in the wrong password the whole time! 
Oh well, I may have wasted a day, but man it's good to have the internet back on a real computer (I had been using the slowest machine since Babbage invented them to post).
Todays lesson: check the simple things first.

Luke

---

### Post by b3tzi on 2006-11-18
Try this script:
[http://www.moigeeknevro.com/speedtouch-ng/files/1.3.1/speedtouch-ng_1.3.1_all.deb](http://www.moigeeknevro.com/speedtouch-ng/files/1.3.1/speedtouch-ng_1.3.1_all.deb)

After the install:
> 
sudo update-rc.d -f pppd-dns remove
sudo update-rc.d pppd-dns start 39 S .


Reboot your computer and it should work. ;)

---

