---
title: "Networking Trouble (Live CD)"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by billy_talent on 2006-08-23
I am running Ubuntu off a live-CD on my AMD Athlon 64. I am having troubles getting my internet to work. The device is activated, but there is no connection. My motherboard has onboard ethernet (Asus ASRock 939Dual-SataII). Is there anything I can do to get my connection to work? 

Note: I am not too technologically literate. Please make this easy and possible to do in the GUI.

---

### Post by ciscosurfer on 2006-08-23
Your card may not be suitable (but then again, it might be b/c you say it is activated) So let's try this first:
Go to Applications > Accessories > Terminal.  And in the terminal window, copy and paste the following in an effort to "bring up" the interface.  Enter the first command, then press Enter.  Enter the second command, then press Enter, and so on.  Now try to browse to your favorite Web site via a browser (Firefox is my favorite browser)```
sudo ifdown eth0
sudo ifup eth0
sudo ifdown eth1
sudo ifup eth1
```If that doesn't work, we need to examine whether your card is "Linux/Ubuntu-ready".
Go to Applications > Accessories > Terminal.  And in the terminal window, copy and paste the following code and then press Enter.  Afterwards, please post here the output from the following command```
lspci | egrep "Ethernet controller"
```Have no fear, we'll figure this out! :D

---

### Post by billy_talent on 2006-08-23
It says "command lspci not found". The other code didnt help.

---

