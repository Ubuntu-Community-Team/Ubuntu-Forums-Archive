---
title: "No Wlan0 Ubuntu 12.04 Atheros Communications Inc. AR9285 Wireless Network"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by nick_aiden on 2013-09-27
Hello I am on ubuntu 12.04 I can't connect to any wifi because I don't have the wlan0 interface. Sorry I am new here.

---

### Post by wildmanne39 on 2013-09-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by swapnil-indore on 2013-09-28
Hi,

Check is the system is able to see you wireless card using this commands

lsusb|grep Atheros
lspci|grep Atheros

Check if the the ath9k module is loaded

 lsmod |grep ath9k


--
[Swapnil Jain]("http://www.techpage3.com/")

---

