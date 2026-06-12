---
title: "Wifi stopped Working Ubuntu 16.04"
date: 2018-08-25
forum: Networking &amp; Wireless
---

### Post by coughsirup on 2018-08-25
Hi,
my Wifi suddenly stopped  working. What changed is, that when I restart my laptop (Thinkpad x220) the Wifi is not enabled. If I enable it via GUI (rightklick on icon -> tick box: 'enable wifi') nothing changes. I do not see any wifi-networks. Internet via ethernet works.

My Wireless-info:
[http://paste.ubuntu.com/p/CdRJCVbzYn/](http://paste.ubuntu.com/p/CdRJCVbzYn/)

I had a look at other Threads, for example this one: [https://ubuntuforums.org/showthread.php?t=2324791](https://ubuntuforums.org/showthread.php?t=2324791)
but for the commands that solved the problems I did not know which module-names to use.
I also tried commands like: 
```

sudo dpkg --configure -a
sudo apt-get dist-upgrade 
sudo apt-get -f install

sudo service network-manager restart 
sudo lshw -class network
nmcli radio wifi off
nmcli radio wifi on

sudo ifconfig wlp3s0 up

rfkill unblock all

```
But so far nothing changed.

Thanks in advance.

---

### Post by jeremy31 on 2018-08-25
Check the wireless switch setting on the left side of the laptop

---

### Post by coughsirup on 2018-08-25
The wireless switch setting is turned on

---

### Post by coughsirup on 2018-08-26
So my wifi works again. I actually don't know what was wrong. I changed the location and suddenly I can find other networks again which is weird because at the recent location my other devices would find the networks except my laptop. However, I am sorry to have wasted your time.

---

