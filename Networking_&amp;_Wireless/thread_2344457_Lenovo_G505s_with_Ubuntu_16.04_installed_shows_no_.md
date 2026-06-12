---
title: "Lenovo G505s with Ubuntu 16.04 installed shows no wireless networks"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by epicmitch on 2016-11-25
I have recently started to getting interested in using Linux and so i thought Ubuntu being the most popular distro should be where i should start. so i got my laptop which i don't really use anymore and installed the latest version of Ubuntu on it which happened to be 16.04. From install i have had no wireless networks appearing even after updates etc. Have i got the wrong drivers or am i doing something wrong or is there anything you can do to help me please?

also I've tried everything stuck to the board and no luck :/

---

### Post by praseodym on 2016-11-25
Please run the wireless-script from the sticky-thread and show the outputs here

---

### Post by epicmitch on 2016-11-25
i'm sorry i've only just started on Linux and have no idea what i'm doing XD. i have no idea what script you mean :/ if you mean "lspci -nn" i did it and go this:

Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

---

### Post by praseodym on 2016-11-25
Try installing this driver:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```
via Terminal. Reboot. Please check if Secure Boot is deactivated for this one!

---

### Post by Hadaka on 2016-11-25
Hi, your wifi card ..Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
performs best with the native brcmsmac driver. To install, please open a terminal...ctrl/alt/t then copy and paste
one line at a time. From a working wired connection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v brcmsmac
```
remove the wired connection and any usb's, boot and test wireless.

*If you are still having difficulties, from a working wired connection please copy and paste..
 ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This builds a file in your home directory named **wireless-info.txt**. please copy  and post.
Thanks.

---

### Post by epicmitch on 2016-11-27
> **praseodym said:**
> Try installing this driver:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```
via Terminal. Reboot. Please check if Secure Boot is deactivated for this one!
Thank you this work a treat and thank you everybody else for trying to help me

---

