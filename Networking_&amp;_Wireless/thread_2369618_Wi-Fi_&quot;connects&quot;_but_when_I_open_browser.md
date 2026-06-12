---
title: "Wi-Fi &quot;connects&quot; but when I open browser I get a jumping t-rex"
date: 2017-08-25
forum: Networking &amp; Wireless
---

### Post by 19gbenson on 2017-08-25
I have no internal card but I have a little adapter and it has been working just fine but this morning when I went to browse the web it didn't work. At first I thought i had to reset the modem but everything else is working totally fine (my family's phones tv etc.) 

Then I thought it was the little Wi-Fi card so I tried to use my phone for usb network tethering but to no avail.

When moving my computer into my furnace room and connecting to to my modem it works just fine... But I don't want to use my computer in my furnace room. 

Thanks in advance for your help

---

### Post by Hadaka on 2017-08-25
Hi please make another trek into the furnace room,
establish a hardwired connection to your router,*Without the
"little wifi adapter" plugged in. *When you are connected to the
internet, plug in the "little wifi adapter". Then..
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
~OR~ use this method..
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
Thanks.

---

