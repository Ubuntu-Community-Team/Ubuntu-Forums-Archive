---
title: "Ubuntu 15.04 TP-LINK WN822N dropping connection"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by j.s.s on 2015-10-03
Hello, first of all I wanted to say that I am new to linux and really want to keep using it, but so far my experience was somewhat limited due to my system lacking basic functionality.

My wi-fi keeps losing connection every 5 minutes or so. I use USB wi-fi dongle TP-LINK WN822N on Ubuntu 15.04. I have dual boot and the Internet on Windows works perfectly. When I turn my wi-fi off and on (in networks settings) it works again for limited time. Most of the time I do not really disconnect from network, I just don't have access to the Internet, once I waited for some more time and it told me that my network is "out of range".

I tried various solutions but none of them worked but as I am linux newbie I may have not executed everything as it should've been done. Today I reinstalled Ubuntu, updated it and tried to install Realtek drivers, but had some error. I am getting really tired of this, so please can someone help me?

[ATTACH=CONFIG]264802[/ATTACH]

---

### Post by praseodym on 2015-10-03
Hi,

change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by j.s.s on 2015-10-03
Thanks, that fixed the problem.

---

