---
title: "Old 2007 iMac, Can't find proper drivers"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by matthew44 on 2014-12-31
So, as I said. Its an old iMac form 2006-07ish installed Ubuntu 14.04 but have no idea where to obtain a proper WiFi driver.

---

### Post by Hadaka on 2014-12-31
Hi, open a terminal..ctrl/alt/t and do,,
```
lspci -nn | egrep '0200|0280'
rfkill list all
lsmod | egrep 'wl|b43'
```
post the output.,
thanks

---

### Post by matthew44 on 2014-12-31
I assume this is what you need.

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by praseodym on 2014-12-31
Install the missing firmware via LAN:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by Hadaka on 2014-12-31
yes, I would have liked the other outputs as well
but this is a start.From a WORKING internet connection
 Please COPY and paste the commands
*praseodym gave you..
thanks

---

### Post by matthew44 on 2014-12-31
> **Hadaka said:**
> yes, I would have liked the other outputs as well
but this is a start.From a WORKING internet connection
 Please COPY and paste the commands
*praseodym gave you..
thanks

So, ah. I tried doing this.. The commands work... But when I task the pc with Reboot or even Shutdown -P (Even going to the top right and clicking either) the pc just goes to a endless loading screen trying to shut down and the changes dont save :|

Oh - and the rest of the output is: 
    
    0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

    ~$ lsmod | egrep 'wl|b43'
    wl                   3999690  1 
    lib80211               14040  1 wl
    cfg80211              409394  1 wl

---

### Post by Hadaka on 2014-12-31
hi, yup thats the problem "wl".....please do,,
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then repeat the commands from praseodym '.

---

### Post by matthew44 on 2014-12-31
Ah, that worked. Thanks!

---

### Post by Hadaka on 2015-01-01
Great ! also dont forget to,,
```
sudo apt-get update
sudo apt-get upgrade
```
please take the time to mark your thread solved
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

