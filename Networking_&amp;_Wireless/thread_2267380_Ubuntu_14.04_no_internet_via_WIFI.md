---
title: "Ubuntu 14.04 no internet via WIFI"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by emil13 on 2015-03-01
Hello,
Firts of all - im noobie in Ubuntu and i'm learning this OS right now ;) 
I have a problem with my internet connection on Ubuntu 14.04. When i'm using wired connection (cable from my notebook to router) i'm online. When I'm connected wireless to my router - i can't load any page. I can't even ping my router and other computers on same network. Im using TP-Link MR3420 router and notebook is Dell Latitude E5420. When i used my smartphone as a router - i had a connection and i was online. Pleas, anyone can help ?

---

### Post by Hadaka on 2015-03-01
hi please do and post..
```
lspci -nnk | grep -iA2 net
rfkill list all
lsmod | egrep 'b43|wl'
```
thanks

---

### Post by emil13 on 2015-03-01
ckbucu@ckbucu-Latitude-E5420:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
--
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
    Subsystem: Dell Device [1028:049b]
    Kernel driver in use: tg3
ckbucu@ckbucu-Latitude-E5420:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
ckbucu@ckbucu-Latitude-E5420:~$ lsmod | egrep 'b43|wl'
wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl

---

### Post by Hadaka on 2015-03-01
Hi, from a working wired conection pease do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get update
```
```
sudo -i 
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
```
sudo modprobe brcmsmac
```

---

### Post by emil13 on 2015-03-01
It works ! Thank you :)

---

### Post by Hadaka on 2015-03-01
Glad that worked for you !
That exact method is in the stickies on the wireless/networks page.
and thank you for marking this solved.

---

