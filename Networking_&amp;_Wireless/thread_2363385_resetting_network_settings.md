---
title: "resetting network settings"
date: 2017-06-09
forum: Networking &amp; Wireless
---

### Post by oddballmotorsports on 2017-06-09
Ok,  so still a newb, (and im sure it shows)  It looks like my problem might be hardware. my problem was slow connection, constantly being kicked off, etc etc. I find this as I'm sitting a foot away from the wireless router.  no problems after an hour.  anyways,  before I discovered this I tried to change a bunch of networking functions, and as a result, some things are not working properly..  what I would like to do is reset network manager to factory default settings.  is there a simple way to accomplishing this? an "idiot proof" way that doesn't involve purging and reinstalling the network manager?   thanks folks!

---

### Post by wildmanne39 on 2017-06-09
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by oddballmotorsports on 2017-06-10
I believe I did this right..   ubuntu 16.04 qualcom atheros  [http://paste.ubuntu.com/24822407/](http://paste.ubuntu.com/24822407/)  :)

---

### Post by Hadaka on 2017-06-10
Hi, please open a terminal ctrl...alt...t  and then copy and paste
one line at a time.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot and test wireless.

When you change out the wifi card the driver for it doesnt just go away.

---

