---
title: "Lubuntu Problem"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by quim_roscas on 2013-10-23
Hello, i downloaded and installed Lubuntu 12.10 for the first time, to replace ubuntu (that worked fine but a little slow) that comes by default in my 
Compaq Mini - 110c, but i´m having problems with the wireless that doesn´t work.
The wireless slider button with the blue light is on, and still can´t get any type of connection, only cable.
Can someone please give some help to fix this ?

Thank you in advance for any help you can provide.;)

---

### Post by wildmanne39 on 2013-10-23
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

