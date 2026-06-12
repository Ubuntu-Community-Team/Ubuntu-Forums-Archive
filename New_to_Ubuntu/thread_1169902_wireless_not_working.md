---
title: "wireless not working"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-25
After installing the restricted extras through synaptic package manager and restarting my computer, my wireless stopped working. Is there anyway i can check what's causing the problem? Right now I'm connected through an ethernet cable

---

### Post by Yvan300 on 2009-05-25
Try reinstalling the wifi driver. Works sometimes.

---

### Post by clhsharky on 2009-05-25
click on network manager that little button top right, and enable wireless.

---

### Post by rlj399 on 2009-05-25
wireless is enabled :-(
how do i know what the wifi driver is called? i'll see if i can find it

---

### Post by 73ckn797 on 2009-05-25
If you have the driver disk that came with the card you can install those drivers in Ubuntu using "ndisgtk" (a GUI installer) found in Synaptic Package Manager. Once installed copy the driver (possibly the Win XP driver) to a folder then run ndisgtk which you will find installed under System/Administration/Wireless Drivers. Select the driver you copied and let it install it.

---

### Post by Steelmourne on 2009-05-25
If wireless is enabled the driver should be enabled. To check run this command:

sudo lshw -C network

the name of the wireless adapter should be there. My Intel 3945ABG was listed. If it says disabled check if there is a switch to turn wireless on. Also check the network settings that you are trying to connect to.

---

### Post by superprash2003 on 2009-05-26
also post output of 
1)iwconfig
2)sudo iwlist scanning

---

### Post by rlj399 on 2009-05-26
ok it seems the problem was only temporary, it's working again. However my concern is that different things have been acting up. For example, after the wireless problem, I was chatting and my screen suddenly got super pixely...I don't even know what it's called but kind of like when your tv doesn't have signal. Could i have a virus or something?

---

