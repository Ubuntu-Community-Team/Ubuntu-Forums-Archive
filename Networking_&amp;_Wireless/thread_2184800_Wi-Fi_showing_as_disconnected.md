---
title: "Wi-Fi showing as disconnected"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by tracey.farrelly on 2013-10-30
I installed ubuntu and my wireless was not working. I tried purchasing a new wireless card and installed it but I am having the same problem. When I click on the network icon I see Wi-Fi Networks and Disconnected underneath. I have installed Broadcom drivers but this doesn't seem to have worked. I have tried removing it from the blacklist. I'm sorry if this sounds newbietastic and like I haven't a clue what I'm doing but, well, I don't.
I am currently using the wired network.
Please help!
Thanks

---

### Post by wildmanne39 on 2013-10-30
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

