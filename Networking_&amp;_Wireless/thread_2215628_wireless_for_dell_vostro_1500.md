---
title: "wireless for dell vostro 1500"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by larryclydeu on 2014-04-07
Hello,

I am a complete novice concerning Ubuntu.  I read in one of your posts  where you were able to get someone's wireless to work.  I have loaded  13.10 on my Dell laptop Vostro 1500, which I believe has Broadcom BCM  4311.  I have figured out how to get to terminal, and have tried running  some of the code suggested but have had no success.  Please help.

  

Thanks,

larryclydeu

---

### Post by wildmanne39 on 2014-04-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by larryclydeu on 2014-04-07
I think I attached the info file.

Thanks

---

### Post by wildmanne39 on 2014-04-07
Please do:
```
sudo apt-get install linux-firmware-nonfree
```
Watch for errors.
Reboot

---

### Post by larryclydeu on 2014-04-07
Thanks, that got my wireless going!  I marked the thread as solved.

---

### Post by wildmanne39 on 2014-04-07
Your welcome!

---

