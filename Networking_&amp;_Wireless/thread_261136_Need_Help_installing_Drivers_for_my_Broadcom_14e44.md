---
title: "Need Help installing Drivers for my Broadcom 14e4:4318 Wireless card"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by cobbweb on 2006-09-19
Hello, 
   I have a Broadcom wireless card bcm43xx (if that makes sense doesn't to me might to you) I have been trying to install everything for it, but and having trouble getting though it. I don't have an internet connection on my computer the driver is being installed on, but I have gotter the file with the XP driver in it. I was also able to install ndiswrapper from the Ubuntu Cd. I really need help on this one, would anyone be willing to help guide me though this? Thank you, 
 
 Cobbweb

---

### Post by sjieke on 2006-09-20
Hello,
I also have a card with broadcom chipset (bcm43xx). I got it working using the following steps.
1) remove the bcm43xx default loaded driver
```
sudo rmmod bcm43xx
```
2) add the bcm43xx driver to the blacklist so it won't load on next boot
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
3) install and configure ndiswrapper using the guide found on the wiki: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")

Hope this helps you, if you need more info just ask ;)

---

