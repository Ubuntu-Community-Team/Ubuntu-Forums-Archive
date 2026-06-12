---
title: "Wifi is not detected in my desktop[using usb wifi adapater supporting RTL8192EU]"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by saugata28 on 2017-02-11
Dear Altruists

I am using a SImplecom nw382 802.11 usb wifi adapter in my desktop. Its succesfully operating in windows environment. But in UBuntu 16.04 environment the wifi is not detecting.I assume that I did not install the hardware correctly.

A. I have tried to install the following provided driver, "20140812_rtl8192EU_linux_v4.3.1.1_11320" following the readme note.
```

1. tar zxvf 20140812_rtl8192EU_linux_v4.3.1.1_11320.tar.gz
   and cd to 20140812_rtl8192EU_linux_v4.3.1.1_11320
2. make
3. su-> enter your root password
4. make install

```
But the make fails showing bunches of errors. The output link is provided [URL="https://drive.google.com/open?id=0B2dtrB0l5aqVWVFQQm85WlNYSjg"]here
[/URL]
B. Then I try the following command: sudo apt-get update
And the output comes following:
```

Hit:1 http://au.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://au.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://au.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Get:4 http://au.archive.ubuntu.com/ubuntu xenial/main Translation-en_AU [420 kB]
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:7 http://au.archive.ubuntu.com/ubuntu xenial/restricted Translation-en_AU [2,012 B]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.0 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [48.1 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:12 http://au.archive.ubuntu.com/ubuntu xenial/universe Translation-en_AU [3,039 kB]
Get:13 http://au.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_AU [67.7 kB]
Fetched 3,816 kB in 9s (385 kB/s)                                              
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

```
C. Then I have tried the following command
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info &&./wireless-info
--2017-02-12 11:10:41--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info

```
to diagnosis the network status and the result show [here]("https://drive.google.com/open?id=0B2dtrB0l5aqVUE9pR2pGNVVXcEU")

And ultimate result appears that the network icon have totally been gone from ubuntu. The screen shot is [URL="https://drive.google.com/open?id=0B2dtrB0l5aqVYXQwLVM5djdqcWc"]here
[/URL]
Currently I am using mobile internet using my mobile as a modem in my desktop in Ubuntu 16.04 environment.

I am looking for sincere advices from you.

Thank You,

---

### Post by praseodym on 2017-02-12
Try this PPA:
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi 
sudo apt-get update
sudo apt-get install rtl8192eu-dkms
```
Reboot

---

