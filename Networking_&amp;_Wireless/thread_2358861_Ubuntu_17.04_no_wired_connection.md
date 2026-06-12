---
title: "Ubuntu 17.04 no wired connection"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by vandavv on 2017-04-18
Hi
After upgrade to 17.04, my wired connection stopped working. Everything's ok with my cable, since I used it previously, also my laptop is pretty new so there shouldn't be any hardware problems.

[http://paste.ubuntu.com/24405956/](http://paste.ubuntu.com/24405956/) - wireless-info.txt

---

### Post by praseodym on 2017-04-18
Hi,

change the driver (if wireless works):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb
sudo dpkg -i r8168-dkms_8.043.02-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by raccoonstrait on 2017-04-18
Not sure if you have the same issue as I did, but there is a bug out there. See response #2 on this thread, it solved my issue.

[https://ubuntuforums.org/showthread.php?t=2358631](https://ubuntuforums.org/showthread.php?t=2358631)

RaccoonStrait

---

