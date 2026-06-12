---
title: "Qualcomm Atheros AR9462: Flaky Internet Ubuntu 12.04"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by Brian_Wong on 2013-09-20
Hello!  I have Ubuntu 12.04 dual booted with Windows 7.  Each time I turn my laptop on it takes a few minutes to connect to the wifi, and the connection drops every couple minutes.  I don't have these problems on my Windows 7 partition.  I would be very grateful for any advice--I would love to continue using Ubuntu as my main OS but I've only been able to use Windows 7 because of this internet problem.  Thank you so much in advance!!

---

### Post by Hadaka on 2013-09-20
Hi,, please post the output of..
```
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by Brian_Wong on 2013-09-20
01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adap
ter [168c:0034] (rev 01)
        Subsystem: Bigfoot Networks, Inc. Device [1a56: 2003]
        Kernel driver in use: ath9k
        Kernel modules: ath9k

---

### Post by Hadaka on 2013-09-20
Hi give this a try..
```
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1
```
*Don't boot and let it run for an hour or so...
IF and only if, it stays connected then do..
to make it permanent
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
enter one line of code.
```
options ath9k nohwcrypt=1
```
save and close gedit...boot

---

### Post by Brian_Wong on 2013-09-20
I followed your instructions, but the problem persists.  Please let me know if there is anything else I can try.  Thanks for your time!

---

### Post by Hadaka on 2013-09-20
Hi, about the only other thing i can suggest is to
set your router to wpa2 only  (not mixed) and use channel 1 or 11
not alot of options for the ath9k driver...sorry.

---

### Post by varunendra on 2013-09-21
You may try compiling the latest backported version, it seems to work better : [http://ubuntuforums.org/showthread.php?t=2173686&p=12785322#post12785322](http://ubuntuforums.org/showthread.php?t=2173686&p=12785322#post12785322)

---

