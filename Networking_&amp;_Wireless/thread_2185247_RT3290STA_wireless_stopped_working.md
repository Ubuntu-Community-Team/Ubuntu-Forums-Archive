---
title: "RT3290STA wireless stopped working"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by Nakira89 on 2013-11-01
Hi all, i have previously followed these instructions 

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

Each time i have updated i have had to re run some of the commands, however on my latest update, i cannot find anyway to get the wireless card working again. 

Is there anything i can do to get this working again? USB tethering with my phone will only last so long :/

Thanks in advance, 
Josh

p.s. Laptop is a HP Envy M6 and running 12.04 iirc

---

### Post by wildmanne39 on 2013-11-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Nakira89 on 2013-11-02
Script has ran fine, i hope you have some luck finding out what is wrong with this. :)

Thank you

---

### Post by dhira on 2013-11-02
HI! I upgraded my system to 1:24.0+build1-0ubuntu0.12.04.1 Thereafter Wireless radar is showing no connections. But it works fine if I swith to older version of Ubuntu. 
I have HP 655 notebook with  RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
What should I do?

---

### Post by Nakira89 on 2013-11-02
> **dhira said:**
> HI! I upgraded my system to 1:24.0+build1-0ubuntu0.12.04.1 Thereafter Wireless radar is showing no connections. But it works fine if I swith to older version of Ubuntu. 
I have HP 655 notebook with  RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
What should I do?


Thats basically what im doing at the moment is swithing to an older kernel version on boot up. Its a pain in the ass i know, but atleast its something for now until we find some kind of work around.

---

### Post by dhira on 2013-11-02
Done! I ran the script and found my Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290] I searched the forum for this controller. I found the instructions and managed to install the driver. Now I just have to lock the latest kernel version and this will prevent driver being erased with the next update. Thanks Wild Man! God bless you all! Dhira

---

### Post by wildmanne39 on 2013-11-02
Please remove that driver completely and try this one:
[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)
if you have any questions please post.
Thanks

---

### Post by praseodym on 2013-11-09
There was a syntax error in that instructions, now its corrected

---

