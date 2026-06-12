---
title: "Wireless Not working"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by iamnidhi22 on 2013-12-26
Hi All,

I have Ubuntu 12.04. After downloading updates from Ubuntu Software Center my wireless is not working. Before downloading the updates it was working fine. Now I am not able to see the Mobile Network and Wireless option, though Wired connection is working fine. Please help me to resolve this problem. 

Current network manager version is 0.9.4.0-0ubuntu4.3.

---

### Post by wildmanne39 on 2013-12-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by iamnidhi22 on 2013-12-27
Thanks for the guidence. Please find the attached wireless info file.

[ATTACH]248944[/ATTACH]

---

### Post by wildmanne39 on 2013-12-27
Hi, please follow the directions in post 9 of the link below and that should get your wireless working.
[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)
Thanks

---

### Post by iamnidhi22 on 2013-12-27
Hello, Thanks for the help..

While following the post 9 of above link I got following error. Please suggest what should I do. 

sudo apt-get remove --purge linux-backports-modules-cw-3.6-`uname -r`



Selecting previously unselected package linux-headers-3.2.0-57-generic. 
 Unpacking linux-headers-3.2.0-57-generic (from .../linux-headers-3.2.0-57-generic_3.2.0-57.87_amd64.deb) ... 
 Selecting previously unselected package linux-headers-generic. 
 Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.57.68_amd64.deb) ... 
 Setting up linux-headers-3.2.0-57 (3.2.0-57.87) ... 
 Setting up linux-headers-3.2.0-57-generic (3.2.0-57.87) ... 
 Examining /etc/kernel/header_postinst.d. 
 run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic 
 Error! Bad return status for module build on kernel: 3.2.0-57-generic (x86_64) 
 Consult /var/lib/dkms/oem-bt-dw1705/0.1/build/make.log for more information. 
 Error! Bad return status for module build on kernel: 3.2.0-57-generic (x86_64) 
 Consult /var/lib/dkms/alsa-hda-lts-quantal/0.1/build/make.log for more information. 
 Error! Bad return status for module build on kernel: 3.2.0-57-generic (x86_64) 
 Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information. 
 Setting up linux-headers-generic (3.2.0.57.68) ...

---

