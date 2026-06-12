---
title: "Lenovo Ideapad Yoga 11S - Ubuntu fresh install - No WiFi"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by angussenn2 on 2015-01-08
Hi,

I have recently installed Ubuntu 14.04 and removed Windows 8.1 from my Lenovo Ideapad Yoga 11S. I however can not get any internet access. The laptop model has no Ethernet port too. I have been searching the internet on my brothers laptop for any solutions but have found none. No additional drivers are available. I know these threads are common but I need to get the Internet back on my laptop so I can get the full Ubuntu experience. Please help

---

### Post by jeremy31 on 2015-01-08
Open a terminal window and enter ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
``` and see if wifi works

---

### Post by angussenn2 on 2015-01-08
Still no network devices found

---

### Post by jeremy31 on 2015-01-08
Follow the instructions on how to use the wireless script without an internet connection
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

