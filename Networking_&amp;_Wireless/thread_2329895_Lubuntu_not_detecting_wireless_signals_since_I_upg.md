---
title: "Lubuntu not detecting wireless signals since I upgraded my system to 16.04"
date: 2016-07-05
forum: Networking &amp; Wireless
---

### Post by cybertripp on 2016-07-05
Hello,

Two days ago I decided to upgrade the lubuntu version in my HP 245 G1 Notebook from 15.x to 16.04 and since then I am only able to connect to the internet with a wire, but no wireless connections show up. Here is my wireless hardware information [http://paste.ubuntu.com/18601496/](http://paste.ubuntu.com/18601496/). I've tried following the instructions of all the forums I found online, but none of the procedures seem to work. I hope that someone in this forum is able to help me.

---

### Post by chili555 on 2016-07-06
Please open a terminal and do:```
sudo -i
apt-get purge bcmwl-kernel-source
echo rt2800pci  >>  /etc/modules
exit
```Reboot and show us:```
sudo iwlist scan
```

---

