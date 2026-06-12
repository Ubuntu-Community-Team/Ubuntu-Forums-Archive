---
title: "BCM43228 wifi not supported, but it worked in install! 12.04"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by fallenstardust on 2014-03-09
I've been trying to get my BCM43228 to work, but failing. it worked during install of 13.10 then died when it was installed. now on 12.04


following the instructions below i installed the STA drivers, that didn't work, then the b43, that didn't work either.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

am i stuffed?

---

### Post by fallenstardust on 2014-03-09
i did this too after the b43

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers)

---

### Post by wildmanne39 on 2014-03-09
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by fallenstardust on 2014-03-11
hey, here is the txt file, it won't let me right click on the file (at all) to zip it. is this a bug or does ubuntu not do right clicking in places?

sorry it took me so long!

---

### Post by fallenstardust on 2014-03-11
scrap the right clicking thing, it doesn't work on firefox either. this a problem.

---

### Post by wildmanne39 on 2014-03-12
Please do:
```
sudo apt-get install bcmwl-kernel-source
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Watch for errors.
Reboot

---

### Post by fallenstardust on 2014-03-12
thanks! i've got wifi! bless your furry socks!

---

### Post by wildmanne39 on 2014-03-12
Your welcome!

---

