---
title: "WiFi Connected - No Internet"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by cessanfrancisco on 2014-02-15
Hi,

I am using Ubuntu 13.10 on a Lenovo Z580.

Periodically, despite the fact the WiFi indicator shows a strong signal, I have no internet connection.  I can tell because Firefox, Chromium, and Opera do not load and Thunderbird cannot connect.

Can anyone give me some insight on how to determine if it's my computer, my router, my ISP, or something else.  I do know that when I restart, log out/in, and/or disable/re-enable the wireless the problem is sometimes remedied.

Thanks in advance.

---

### Post by wildmanne39 on 2014-02-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

