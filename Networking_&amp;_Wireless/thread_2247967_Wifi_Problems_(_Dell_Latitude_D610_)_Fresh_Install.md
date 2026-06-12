---
title: "Wifi Problems ( Dell Latitude D610 ) Fresh Install"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by Antonio_Patterson on 2014-10-11
Hello Guys , I am a noob at Ubuntu / Linux desktop... I have work a bit with Ubuntu server. I have installed Ubuntu on my Dell Mini before with no problem but now I have installed it on my Dell Latitude D610 and now the wireless does not work.. I cant use wifi at all. I can only access the internet via Ethernet , which I am using now. I have tried tons of things that I have found on the forums and non of them have worked. I dont know what else I can do but I need to be able to use wireless with this computer. Here is a picture of my computer specs ... (  [http://imgur.com/CCUmMWZ](http://imgur.com/CCUmMWZ) )

---

### Post by jeremy31 on 2014-10-11
Follow the instructions to download and run the wireless script [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

If you are not familiar with attaching files and the code tags it might make it easier if you install pastebin before using the script ```
sudo apt-get install pastebinit
```
When the script is done it will ask if you want to upload to pastebin, choose Y and press enter and it will show a URL in terminal that you can copy and paste into a post with your mouse

---

### Post by Antonio_Patterson on 2014-10-11
[http://paste.ubuntu.com/8540732/](http://paste.ubuntu.com/8540732/)

---

### Post by wildmanne39 on 2014-10-11
Please do:
```
sudo apt-get install firmware-b43legacy-installer
```
Then reboot.

---

### Post by Antonio_Patterson on 2014-10-11
Alright

---

### Post by Antonio_Patterson on 2014-10-11
Omg , Thank you ... I had to enter my info and it wouldnt connect then I rebooted and now it works! Thank you so much!

---

