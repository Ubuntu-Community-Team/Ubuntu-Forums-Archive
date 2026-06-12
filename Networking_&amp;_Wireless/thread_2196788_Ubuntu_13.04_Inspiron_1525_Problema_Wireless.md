---
title: "Ubuntu 13.04 Inspiron 1525 Problema Wireless"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by pauloccp52 on 2013-12-31
Caros colegas,

I have the following problem:

I installed Ubuntu 04.13 on Inspiron 1525. He does not recognize the wireless signal here at home. As I am new to the subject, takes a lot of help from colleagues.

hugs

---

### Post by wildmanne39 on 2013-12-31
I used google translate to translate your post to English so people will understand and you can get the help you need, this is an English forum, please use google translate to translate your messages before you post here.
Thanks

---

### Post by wildmanne39 on 2013-12-31
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

