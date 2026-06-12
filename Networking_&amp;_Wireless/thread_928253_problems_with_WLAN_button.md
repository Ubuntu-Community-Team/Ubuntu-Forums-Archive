---
title: "problems with WLAN button"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by shazy on 2008-09-23
hi, i used to use windows vista on my laptop (compaq presario). 2 or 3 weeks i uninstalled windows vista and installed Ubuntu in my laptop. now since i have installed Ubuntu, the WLAN button does not work. when i used to use vista the button used to work very well, the blue light used to switch on whenever i pressed the WLAN button but now no matter how much i press the button there is no blue light nor is there any internet connection detected. please help. all the help will be very much appreciated. i am soooo worried!! thanking you...

---

### Post by willca on 2008-09-24
mind you bro...most PCs nowadays are manufactured to windows specs...thats why the button for your wireless dont work like magic.

try this to see if your wifi nic is even getting recognized..

iwconfig
ifconfig
sudo iwlist wlan0 scan (assuming your wifi nic is called wlan0)

If nothing comes out of these...then do this

lspci | grep Ethernet 

and post it here.

If it happens to be a Broadcom chip...then try this.

sudo apt-get install b43-fwcutter

and follow the steps.

---

### Post by superprash2003 on 2008-09-24
also type lshw -C network in your terminal and post output

---

