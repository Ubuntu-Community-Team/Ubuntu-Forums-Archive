---
title: "tp link wn725n not connecting but picking up signals"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by daniel109 on 2014-01-31
So i am new here and new to linux in general , so sorry if this is a stupid question to ask . 

i have recently set up xUbuntu 12.04 on my PC and now i am trying to  connect to the internet, i have the TP-Link wireless usb adapter , model  TL-WN725N , and connections show up but i can not connect to them ,  every time i try it fails, no error , simply does not connect and there are times when there are no wifi signals picked up at all , this is probably as i have no driver  installed , can anyone tell me where to download drivers that will work  on xubuntu or how to fix this issue otherwise . I have been reading up on ndiswrapper but i am terribly confused . 

thanks for any help

-Dan

---

### Post by praseodym on 2014-02-01
Hi,

please show the terminal outputs of
```

uname -a
lsusb
```

---

### Post by daniel109 on 2014-02-02
> **praseodym said:**
> Hi,

please show the terminal outputs of
```

uname -a
lsusb
```

uname -a 

i get this  :

```
Linux Daniel 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 25 16:23:24 UTC 2013 i686 i686 i386 GNU/Linux 
```

and for lsusb 

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN


```

thanks for any help

---

### Post by praseodym on 2014-02-02
Install this updated driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by daniel109 on 2014-02-03
> **praseodym said:**
> Install this updated driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

i got this : 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build-essential' has no installation candidate
E: Unable to locate package dkms
daniel@Daniel-Rossi:~$ 


```

i didnt reboot as from what i can see nothing has been installed so there would be no point in doing so .

---

### Post by praseodym on 2014-02-03
Open the update-manager->Settings

Choose there "Software from Ubuntu" and tick the first 4 ones (without "source"). Close it and run
```

sudo apt-get update
```Then try again.

---

### Post by daniel109 on 2014-02-03
> **praseodym said:**
> Open the update-manager->Settings

Choose there "Software from Ubuntu" and tick the first 4 ones (without "source"). Close it and run
```

sudo apt-get update
```Then try again.

now i got this (if i did not mention i am currently not connected to the interent , probably why the update failed) : 

```
Err http://security.ubuntu.com precise-security Release.gpg
  Could not resolve ‘security.ubuntu.com’
Err http://extras.ubuntu.com precise Release.gpg
  Could not resolve ‘extras.ubuntu.com’
Err http://gb.archive.ubuntu.com precise Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com precise-updates Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com precise-backports Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Err http://gb.archive.ubuntu.com precise-proposed Release.gpg
  Could not resolve ‘gb.archive.ubuntu.com’
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Could not resolve ‘security.ubuntu.com’

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not resolve ‘extras.ubuntu.com’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/precise-proposed/Release.gpg  Could not resolve ‘gb.archive.ubuntu.com’

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by praseodym on 2014-02-03
Any chance to connect via cable?

---

### Post by daniel109 on 2014-02-03
> **praseodym said:**
> Any chance to connect via cable?

very little,  any other way around it , like downloading the files on my laptop to my usb then transferring them , or would that not work ?

---

### Post by praseodym on 2014-02-03
Only this lines would be enough:
```

sudo apt-get update
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
```
Some 2minutes or so. "build-essential" is a metapackage installing aound 15 files...

---

### Post by daniel109 on 2014-02-06
> **praseodym said:**
> Only this lines would be enough:
```

sudo apt-get update
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb
```
Some 2minutes or so. "build-essential" is a metapackage installing aound 15 files...

won't i still need an internet connection for this ?

---

### Post by praseodym on 2014-02-06
Yes, thats why I asked for LAN. Any chance for it? Or try these first:

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb)
[https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb)

Save them in "Downloads" and
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by daniel109 on 2014-02-07
well thanks anyway got it sorted

---

