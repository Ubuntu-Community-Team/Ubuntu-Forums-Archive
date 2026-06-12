---
title: "Lost wireless connection after Ubuntu update, how to restore it?"
date: 2017-02-09
forum: Networking &amp; Wireless
---

### Post by vaslanzadeh on 2017-02-09
Hello,

After I updated Ubuntu, I lost my wireless connection. I still can connect with Ethernet cable but I can not see list of available wireless networks.
I did try to follow suggestions already in the forum and updated the system as below but still wireless network is not working.
 
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get purge bcmwl-kernel-source

I have dual boot Linux and Windows on G510 Lenovo laptop. 

In Additional Drivers tab I have:
Broadcom Corporation: BCM43142 802.11b/g/n
This device is using an alternative driver.
Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

I am new to Ubuntu, any help would be very appreciated.

---

### Post by praseodym on 2017-02-09
bcmwl-kernel-source is (too) old, try this one instead:

```
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://ubuntu-master.mirror.tudos.de/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-5_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-5_all.deb
```
Reboot

---

### Post by vaslanzadeh on 2017-02-09
Thank you, this did not solve the problem. But I found a solution :guitar:I had to disable UEFI Secure Boot in BIOS suggested here ([https://ubuntuforums.org/showthread.php?t=2331302](https://ubuntuforums.org/showthread.php?t=2331302))

---

