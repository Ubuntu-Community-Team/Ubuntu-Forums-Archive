---
title: "Lenovo Z510 BCM43142 Wireless Issue"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by ken24 on 2013-12-06
So, I just got a Lenovo Z510 and as it turns out, it has the infamously non-supported BCM43142 wireless card. I'm running 64 bit 13.10 Unity (entirely in live for now).

I have scoured the forums for solutions, but none have specifically worked for either 13.10 or for my specific laptop. In most cases solutions didn't match either.

Is there any fix that anyone is aware of so that I can get off the cable and start enjoying the distro? 

I don't really know what information the forums like to have for a problem like this, so I will run any commands that will help out.

Thanks very much in advance.

---

### Post by chili555 on 2013-12-06
How about this information:```
lspci -nn | grep 0280
```

---

### Post by ken24 on 2013-12-07
Output is as follows:

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

Thanks for the quick response.

---

### Post by chili555 on 2013-12-07
With the cable hooked up, please open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and your wireless should be working.

---

### Post by ken24 on 2013-12-07
Thank you very much, worked perfect.

---

### Post by chili555 on 2013-12-07
> **ken24 said:**
> Thank you very much, worked perfect.My pleasure! Glad it's working.

Please mark the thread Solved; the searchers will appreciate it. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Andy_Arshavin on 2014-11-01
> **chili555 said:**
> With the cable hooked up, please open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and your wireless should be working.


When I do that, then show this message
"Media change: please insert the disc labeled
 'Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20141005)'
in the drive '/media/cdrom/' and press enter" - - how can i fix it? I try to mount ubuntu 14.10 to my cd rom but stil didn't work, thanks

---

### Post by chili555 on 2014-11-01
> **Andy_Arshavin said:**
> When I do that, then show this message
"Media change: please insert the disc labeled
 'Ubuntu 14.10 _Utopic Unicorn_ - Alpha i386 (20141005)'
in the drive '/media/cdrom/' and press enter" - - how can i fix it? I try to mount ubuntu 14.10 to my cd rom but stil didn't work, thanksFirst, open Software and Updates. Make sure that 'Installable from CD-ROM/DVD' is un-checked. Next, rebuild the database:```
sudo apt-get update
```And try again:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

