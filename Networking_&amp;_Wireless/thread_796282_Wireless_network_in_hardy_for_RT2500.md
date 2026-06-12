---
title: "Wireless network in hardy for RT2500"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by mmarif4u on 2008-05-16
I will not go for more explanation,i already post this problem b4 (4 weeks ago), but with no solution.
Link is:
[Link for previous thread]("http://ubuntuforums.org/showthread.php?p=4731796").
> RaLink RT2500 802.11g Cardbus/mini-PCI 
But later i switch back to gutsy.now i am thinking to upgrade to 8.04.
Any body have a solution for this problem.

---

### Post by chili555 on 2008-05-16
There is evidently a better rt2500 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Now, whether you upgrade, install *backports* and your troubles are over, I don't know; I just see there is an improved rt2500 there. Please let us know.

---

### Post by mmarif4u on 2008-05-16
You mean install that from internet.But i don't have Ethernet.Just wifi,which is not working.I can download from some where backports.if any body knows any link to them.

---

### Post by chili555 on 2008-05-16
You can get it here: [http://packages.ubuntu.com/hardy/devel/linux-backports-modules-hardy-generic](http://packages.ubuntu.com/hardy/devel/linux-backports-modules-hardy-generic) and you will also need: [http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic) You will get .deb files, which you can install with:```
sudo dpkg -i <ur_package>.deb
```Let us know.

---

