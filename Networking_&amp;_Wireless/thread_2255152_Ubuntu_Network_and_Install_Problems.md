---
title: "Ubuntu Network and Install Problems"
date: 2014-12-02
forum: Networking &amp; Wireless
---

### Post by Tony_Fendall on 2014-12-02
I now have Ubuntu up and running. I found the following commands to install wireless Broadcom 4311 drivers.
All I need to do now is to get Ubuntu to shut down properly.  It currently continues dotting left to right under the logo.
It does work if I kill the power on the laptop power switch and it does boot properly next time I use it.
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer

---

### Post by Hadaka on 2014-12-02
Hi, Is your wired connection workng??

---

### Post by Tony_Fendall on 2014-12-02
Yep up and running on wireless.  Nearly fixed, only taken me 6 months, but Summer interviened.

---

### Post by Hadaka on 2014-12-02
ok. you said "All I need to do now is to get Ubuntu to shut down properly.  It currently continues dotting left to right under the logo"
to help with that, from a WIRED connection,connected to the internet
please COPY and paste one line at a time into a terminal
please do..
```
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
```
this will kill your wireless..but thats what we want it to do..then do
```
sudo apt-get update
sudo apt-get upgrade
```
boot
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```
boot and test.
thanks.

---

### Post by Tony_Fendall on 2014-12-03
Done similar to above and laotop shuts down, however from 100% battery the laptop battery was at zero this morning.  So shut down but still under power overnight.
On mains and charging all is running properly, but complete shutdown i.e. killing battery power not achieved yet.  Others are having the same problem, I believe.

---

### Post by Bucky Ball on 2014-12-03
> **Tony_Fendall said:**
> On mains and charging all is running properly, but complete shutdown i.e. killing battery power not achieved yet.  Others are having the same problem, I believe.

Appears to be the case, yes.

---

