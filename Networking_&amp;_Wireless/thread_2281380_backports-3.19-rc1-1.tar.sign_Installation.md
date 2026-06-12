---
title: "backports-3.19-rc1-1.tar.sign Installation"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by marv2 on 2015-06-06
Hi,on my former Win8 Samsung laptop I installed Ubuntu 12.04. LTS, which does not recognise my WLAN-chip. The ATH9K driver in 14.04. does - but my vodafone usb stick used for surfing the web develops a life of its own so I kept my 12.04.But how do I install the file (see title) - the information provided does not answer my questions - I simply don' t get it !Can you explain in easy steps how to install this file - I am going on vacation soon and would be pleased if I were able to use the - free - hotel WLAN...Thanks a lot !

---

### Post by chili555 on 2015-06-06
Without knowing details of your device, I can't speculate if the backports package will solve your issue, but I'm happy to describe the process in general. First, you do not want the .sign package; you want this: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz) Download it to your desktop and right-click it and select 'Extract Here.'

Now, with a temporary internet connection by ethernet or whatever means possible, open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
cd ~/Desktop/backports-3.19-rc1-1
make defconfig-ath9k
make
sudo make install
sudo modprobe ath9k
```You will have compiled the for your currently running kernel only. When Update Manager installs a later kernel version, also known as linux-image, after the requested reboot, you must recompile:

```
cd ~/Desktop/backports-3.19-rc1-1
make clean
make defconfig-ath9k
make
sudo make install
```

Reboot again and your wireless will again be working. Please retain the file and these instructions for that time.

---

