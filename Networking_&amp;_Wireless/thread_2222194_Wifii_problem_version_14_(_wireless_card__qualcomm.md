---
title: "Wifii problem version 14 ( wireless card : qualcomm atheros ar242x)"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by marco40 on 2014-05-05
Hello, today I installed for the first time Lubuntu on my Aspire One. 
It seems to be fast and running in every aspect, but not for the wifii 


I tried to solve the problem by reading other posts, but without a result. :(
Some of you might help me in more detail?  

If you need more information to understand the problem, do not hesitate to ask me
Thanks in advance to all ;)

---

### Post by wildmanne39 on 2014-05-05
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

