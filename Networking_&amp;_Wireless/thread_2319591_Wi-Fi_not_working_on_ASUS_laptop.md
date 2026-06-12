---
title: "Wi-Fi not working on ASUS laptop"
date: 2016-04-05
forum: Networking &amp; Wireless
---

### Post by nickmavrick11 on 2016-04-05
I recently installed Ubuntu 14.04 LTS on my ASUS laptop. After installation, the Wi-Fi stopped working properly. It works normally for a few webpages, but after about 5-10 minutes it disconnects and the only way to get Wi-Fi working again is to restart the computer. any suggestiions on how I can fix this?

---

### Post by howefield on 2016-04-06
Thread moved to the "*Networking & Wireless*" forum.

You could read and action[ this sticky]("http://ubuntuforums.org/forumdisplay.php?f=336") to provide more information for others to help you.

---

### Post by Hadaka on 2016-04-06
Hi, please open a terminal ctrl/alt/t then Copy and paste the wireless script command
A file will be written to your home directory.The file name is **wireless-info.txt**
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
Please copy, paste and post the **wireless-info.txt  **
thanks.

---

