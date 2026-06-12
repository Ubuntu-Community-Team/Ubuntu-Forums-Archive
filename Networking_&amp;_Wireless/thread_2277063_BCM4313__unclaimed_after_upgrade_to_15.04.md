---
title: "BCM4313  unclaimed after upgrade to 15.04"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by adiabat2 on 2015-05-06
BCM4313 [14e4:4727] (rev 01) wireless adapter (which was working under 14.10) shows as "unclaimed" in 15.04 under both systemd and upstart boots. 

Wireless-info script output and /etc/modprobe.d/blacklist.conf attached.

Help would be greatly appreciated!!

---

### Post by Hadaka on 2015-05-06
Hi,please COPY and paste the following commands, one at a time
thanks.
```
sudo sed -i '/^blacklist brcmsmac/ d' /etc/modprobe.d/blacklist-bcm43.conf
sudo sed -i '/^blacklist bcma/ d' /etc/modprobe.d/blacklist-bcm43.conf
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

boot

```
sudo modprobe  brcmsmac
```
thanks

---

### Post by adiabat2 on 2015-05-06
Works again. Thanks for the speedy response!

---

### Post by Hadaka on 2015-05-06
Glad that worked for you,please take the time
to mark your thread SOLVED. sign back in..click Thread Tools 
on your original post.
and please run this corrected command..
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
thanks.

---

