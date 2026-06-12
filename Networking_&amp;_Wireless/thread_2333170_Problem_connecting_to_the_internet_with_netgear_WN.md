---
title: "Problem connecting to the internet with netgear WNA3100"
date: 2016-08-07
forum: Networking &amp; Wireless
---

### Post by ahmed.elrmady on 2016-08-07
hey everyone !

i just installed ubuntu 16.04 , and i can't connect to my wireless network , i managed to install it and i already see my network but i can't get access, i checked the password like a million time but no use.

im using a desktop computer dell T5400"

---

### Post by jeremy31 on 2016-08-07
*Thread moved to **Networking & Wireless**.*

Welcome to the forums

See the wireless script link in my signature and post your results.

---

### Post by ahmed.elrmady on 2016-08-07
thank u jeremy31 for such fast response :) , i opened the wireless script and executed this command :
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

as the link u gave me , and it downloaded a text file and a compressed folder.the text file contains a lot of mmm things , well i doesn't make sense for me any way ,and here it is in the attachments 



ohh and i used these instructions to install my usb network adapter in the first place if this will help

[http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter](http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter)  
[https://ubuntuforums.org/showthread.php?t=2052594](https://ubuntuforums.org/showthread.php?t=2052594)

---

### Post by jeremy31 on 2016-08-08
Can you change encryption on the wifi router to WPA2 only?  It is the only idea I have as I once had the same adapter and I mailed it to fellow member chili555 to see if he had better luck with it and this is his report [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

---

### Post by chili555 on 2016-08-08
A quote from the thread:>  I don't believe this device can be made to work correctly in Ubuntu 14.04 and later. Please don't ask me to help. I've tried everything I know of and it doesn't work.There are a few devices that can be obtained for US$10-15 that work perfectly. I recommend that you do so.

---

