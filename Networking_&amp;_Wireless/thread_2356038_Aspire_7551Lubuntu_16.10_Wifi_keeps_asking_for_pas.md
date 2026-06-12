---
title: "Aspire 7551/Lubuntu 16.10 Wifi keeps asking for password"
date: 2017-03-19
forum: Networking &amp; Wireless
---

### Post by eddydewallyvis on 2017-03-19
[http://paste.ubuntu.com/24208206/](http://paste.ubuntu.com/24208206/)

Already tried:

-different modem
-different distro
-lots of solutions found on the internet

Wifi won't connect and keeps asking for password.
On a clean install Lubuntu 16.10 now and followed steps from this thread:

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by wildmanne39 on 2017-03-19
Hello and welcome to the forum, nice job at reading the sticky, please do the following command and I believe your issue will be resolved.
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot
Thanks

---

### Post by eddydewallyvis on 2017-03-19
> **wildmanne39 said:**
> Hello and welcome to the forum, nice job at reading the sticky, please do the following command and I believe your issue will be resolved.
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot
Thanks


Didn't work.

---

### Post by wildmanne39 on 2017-03-19
Please run the wireless script again and post the new file it creates so we can see if the changes stuck.
Thanks

---

### Post by eddydewallyvis on 2017-03-19
> **wildmanne39 said:**
> Please run the wireless script again and post the new file it creates so we can see if the changes stuck.
Thanks

[http://paste.ubuntu.com/24209956/](http://paste.ubuntu.com/24209956/)

---

### Post by wildmanne39 on 2017-03-19
Is telenet-2A42E the network you want to connect too? 

There are some errors showing, I will look at them after I know for sure the name of the network you want to connect too.
Thanks

---

### Post by eddydewallyvis on 2017-03-20
> **wildmanne39 said:**
> Is telenet-2A42E the network you want to connect too? 

There are some errors showing, I will look at them after I know for sure the name of the network you want to connect too.
Thanks

Yep, that's the one.

---

### Post by eddydewallyvis on 2017-03-22
bump

---

