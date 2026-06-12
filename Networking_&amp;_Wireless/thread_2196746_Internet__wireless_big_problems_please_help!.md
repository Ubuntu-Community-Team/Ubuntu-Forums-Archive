---
title: "Internet / wireless big problems please help!"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by dafuqmanlolz on 2013-12-31
Hey, so when I got ubuntu or since I started to install it my wireless button/switch stop working it didn't switch to blue or any colour it's just gray.
So on Ubuntu "LIVE" the test version with the usb bootable when I plug the internet cable it works, but after install it doesn't work.
I saw  "Additional Drivers" so after that I saw wireless driver I press install but it said a error but then my internet cable activated but lets say if i restart my laptop it at additional driver the wireless driver install will dispear then i can activate my cable internet the wierd way.


Here are pictures : 
[http://i.imgur.com/jNosWJo.png](http://i.imgur.com/jNosWJo.png)
[http://i.imgur.com/3mdUiVg.png](http://i.imgur.com/3mdUiVg.png)

Thank you please some proper help !

I haven't had this problem in the past with Ubuntu.

---

### Post by chili555 on 2013-12-31
Let's see which wireless card you have and therefore, which driver you require. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```

---

### Post by dafuqmanlolz on 2013-12-31
```
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


```

---

### Post by chili555 on 2013-12-31
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Is it working now? It may take a reboot.

'Additional Drivers' happily offers the wrong driver for your Broadcom 4311; I recommend you ignore it.

---

### Post by dafuqmanlolz on 2013-12-31
Wow man I can't belive it works!!!! My cable and my wireless works now thank you  very much!!!

---

### Post by wildmanne39 on 2013-12-31
Please use thumbnails or urls for images in the future, large images make it impossible for people with slow internet connections to load the page.
Thanks

---

### Post by chili555 on 2013-12-31
> **dafuqmanlolz said:**
> Wow man I can't belive it works!!!! My cable and my wireless works now thank you  very much!!!

May we get a Solved, please? [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

