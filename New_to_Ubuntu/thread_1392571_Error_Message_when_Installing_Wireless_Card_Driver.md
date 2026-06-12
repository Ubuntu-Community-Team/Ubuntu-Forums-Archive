---
title: "Error Message when Installing Wireless Card Driver"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by glchriste on 2010-01-28
For some reason, when I try to install the driver for my wireless card (and  it matches the card, the driver is made by the same company that makes a specific driver for it), however, for some reason I get an error message when trying to install the driver.

My laptop is dual partitioned, with 20GB being Windows XP and 30GB being Ubuntu, with about 200GB of free space floating around for me to use at my whim. When I'm booting Windows XP, the wireless card (RT2860) and driver works fine (it came preinstalled along with Windows XP, I added on Ubuntu second); yet, when I run Ubuntu, it doesn't have the driver for my wireless card and thus only senses eth0, but I've run into a conundrum because I can't install the driver on Ubuntu, either, as I get this error message.

Help...? [-o<

Wireless Card Information:
802.11n Wireless LAN Card
Ralink Technology Corp
PCI Slot 9 PCI bus 3 device 0 function 0

Driver Provider Ralink Technology Corp
Driver date 3/24/2009
Version 1.4.2.0

rt2860.sys

Driver Information/Link: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

> 
glchriste@ubuntu:~$ dir
Desktop    Downloads         Music     Public      Videos
Documents  examples.desktop  Pictures  Templates
glchriste@ubuntu:~$ cd Desktop
glchriste@ubuntu:~/Desktop$ dir
2009_0918_RT2860_Linux_STA_v2.2.0.0
2009_0918_RT2860_Linux_STA_v2.2.0.0.tar.bz2
2009_0918_RT2860_Linux_STA_WebUI_v2.2.0.0
2009_0918_RT2860_Linux_STA_WebUI_v2.2.0.0.tgz
Artwork
CompilingEasyHowTo_files
CompilingEasyHowTo.htm
how-to-install-source-files-in-ubuntu_files
how-to-install-source-files-in-ubuntu.html
Movies
Music
ndiswrapper-1.55.tar.gz
Programming
tarfileinstall.txt
Torrents
Writing
glchriste@ubuntu:~/Desktop$ cd 2009_0918_RT2860_Linux_STA_v2.2.0.0
glchriste@ubuntu:~/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0$ sudo make install
[sudo] password for glchriste: 
make -C /home/glchriste/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/glchriste/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/glchriste/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/glchriste/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux'
make: *** [install] Error 2
glchriste@ubuntu:~/Desktop/2009_0918_RT2860_Linux_STA_v2.2.0.0$ 


---

### Post by skymera on 2010-01-28
Hi can you post the output of 

```
 lsusb 
``` and ```
 lspci 
```

My wireless card is RaLink and has worked out of the box since 7.04 (Maybe even before)

---

### Post by Hospadar on 2010-01-28
Also are you sure your driver isn't available in the restricted drivers?  System->Administration->Hardware Drivers

---

### Post by glchriste on 2010-01-29
I fixed the driver installation problem, evidently I have 3060, and I installed the appropriate wireless card driver--it worked. However, I still can't search for wireless networks, and thus I can't connect to the internet. Any ideas?

[IMG]http://img69.imageshack.us/img69/789/screenshot1we.png[/IMG]
[IMG]http://img684.imageshack.us/img684/8594/screenshot2ca.png[/IMG]

[IMG]http://img39.imageshack.us/img39/8937/screenshothardwaredrive.png[/IMG]

---

### Post by glchriste on 2010-01-30
Bump. ***I really need help on this one.***

***Any geniuses out***** there?**

---

### Post by glchriste on 2010-01-30
Guess not.......

---

