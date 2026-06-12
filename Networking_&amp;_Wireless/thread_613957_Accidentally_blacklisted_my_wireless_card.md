---
title: "Accidentally blacklisted my wireless card"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by dunnthetown on 2007-11-15
I accidentally blacklisted my wireless card because I used the Feisty No-fluff way to Ndiswrapper. Is there a way to un-blacklist it so I can use the firm-ware instead? Please give me the code that I need to put in the terminal. Thanks a lot.

---

### Post by ddrichardson on 2007-11-15
Yes remove the blacklisted module from /etc/modprobe.d/blacklist and reboot

---

### Post by dunnthetown on 2007-11-15
How do you do that? What code do I use in the terminal to remove it from the blacklist?

---

### Post by ddrichardson on 2007-11-15
```
sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.bak
gksudo gedit /etc/modprobe.d/blacklist
```Edit out the line where your wireless cards module is blacklisted and then save/close gedit. Reboot and there you go.

---

### Post by dunnthetown on 2007-11-15
Thanks a lot!

---

### Post by dunnthetown on 2007-11-15
Wait, it still won't let me use the internet. Just to let you know, I am using Gutsy and performed a Feisty operation in the terminal. I tried to get my wireless card to have a better signal by not using the firmware that Ubuntu provides. What exactly did I do that caused me to lose my wireless? Here is the page that I used:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

wget http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip
unzip Driverv3100640.zip; cp Driver/WinXP/* ./

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

```

Can you see why it blocked my wireless permissions?

---

### Post by ddrichardson on 2007-11-15
That page blacklisted the bcm module and installed ndiswrapper. I take it you have a broadcom card? There is a good guide [here]("http://ubuntuforums.org/showthread.php?t=405990").

---

