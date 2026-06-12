---
title: "no internet connection on fresh Ubuntu 14.04"
date: 2015-10-21
forum: Networking &amp; Wireless
---

### Post by AlexisFFM on 2015-10-21
Hi guys , 

a couple of days ago i installed for the first time Ubuntu OS and the wifi drivers werent installed. I tried to plug in the internet cable in order to connect, but without succes. I look for solution on the internet, but 
could find anything that worked for me. Can u pls help me solve this problem. Thanx in advance !

---

### Post by Hadaka on 2015-10-21
please post the output of,,
```
lspci -n | awk '/0200|0280/ {print $3}'
```
thanks

---

### Post by AlexisFFM on 2015-10-21
> **Hadaka said:**
> please post the output of,,
```
lspci -n | awk '/0200|0280/ {print $3}'
```
thanks

14e4:4359 
10ec:8168

---

### Post by praseodym on 2015-10-21
Download these 2 files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

For 32bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb)

For 64bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot. Wireless should work. After that change the LAN driver via:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot again and LAN should work, too.

---

### Post by AlexisFFM on 2015-10-21
the link to the second file isnt working :( can you check if its correct ? thanks

---

### Post by praseodym on 2015-10-21
Obviously, the servers are not responding, here is the (same) one from 15.04:

32bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_i386.deb)

or 64 bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb)

You only need one of them.

---

### Post by AlexisFFM on 2015-10-21
i did what you say, but still isnt working. Any suggestions what to do next ?

---

### Post by praseodym on 2015-10-21
Did you reboot? Activated "Broadcom-STA" under "Additional drivers" in the software update? Please check:
```

lsmod
rfkill list
iwconfig
route -n
sudo iwlist scan
```

---

