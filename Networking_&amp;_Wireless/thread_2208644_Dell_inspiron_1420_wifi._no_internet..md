---
title: "Dell inspiron 1420 wifi. no internet."
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by Theodore_Lee_Griss on 2014-03-01
ok i have a dell inspiron 1420 and i have installed ubuntu 13.10. along with win 7 Ultimate. I cant get the wifi to work on ubuntu side of os. I have tried three different methods but none have worked. i dont have a hard line to install the wifi driver that way i have to download with win 7 and switch over to ubuntu to try and fix the problem. i need a step by step idiots guide on how to do this because nothing has worked to this point...

---

### Post by wildmanne39 on 2014-03-01
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2014-03-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Theodore_Lee_Griss on 2014-03-01
[ATTACH]250807[/ATTACH][ATTACH]250807[/ATTACH]> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Theodore_Lee_Griss on 2014-03-01
Im new to this forum. I have never had an issue with the wifi like i am now with ubuntu. So i sent the file in the last reply...

---

### Post by wildmanne39 on 2014-03-01
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -rv b43
sudo modprobe -rv ssb
sudo modprobe -v b43
```
watch for errors, continue with all commands even if you receive an error.
Thanks

---

### Post by Theodore_Lee_Griss on 2014-03-01
do you want me to send you the errors?

---

### Post by wildmanne39 on 2014-03-01
If it did not work yes post the errors here using code tags by hitting # and placing the errors between the brackets.
Thanks

---

### Post by Theodore_Lee_Griss on 2014-03-01
Well i am in Ubuntu to reply. Thanks alot. where is a good website to learn more about ubuntu or linux in general?

My GF Gives you many thanks.

---

### Post by wildmanne39 on 2014-03-01
This is for using the terminal but it does not have to be used very often.
[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

I bought two books from Amazon a few years ago but things change so quick I would not do it again except for commands.

Most people start a thread in the Absolute Beginners Section to ask that question and they usually get plenty of replies.
Thanks

---

### Post by KobKol on 2014-10-18
I have to confest that "how to" above is work for my Inspiron 1420 running Ubuntu 14.04.1 LTS
```

saman@Inspiron-1420:~$ uname -a
Linux Inspiron-1420 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

saman@Inspiron-1420:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

saman@Inspiron-1420:~$ lspci -nnk | grep BCM
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)


```

thanks to Wild Man

---

### Post by Paul_McNabb on 2015-03-08
This worked for me - Thank you !

---

