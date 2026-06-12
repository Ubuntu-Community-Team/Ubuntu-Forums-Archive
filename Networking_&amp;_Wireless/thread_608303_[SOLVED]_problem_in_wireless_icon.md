---
title: "[SOLVED] problem in wireless icon ?????????"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by myharshdesigner on 2007-11-09
i hve configer my wireless network it's working fine. but the problem is that the is no icon of wireless network and connection in the top pannel.

so how to solve this problem ?

---

### Post by nae5 on 2007-11-11
no two computers next to clock?  i think that package is called network-manager  go to Applications>Add/Remove>  check box next to Network Manager

---

### Post by myharshdesigner on 2007-11-12
Thanks i ahve solved my problem through with different method

---

### Post by myharshdesigner on 2007-11-12
Colmmand for look for you wireless card :-

lspci -n

iwconfig


if you have some reply's from iwconfig then use this steps :-

Step 1: All BCM43xx - Install NDISWrapper and Blacklist Native Driver

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

Step 2: "BCM4318" Driver Download/Extraction

wget [http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip](http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip)
unzip Driverv3100640.zip; cp Driver/WinXP/* ./


Step 3: All BCM43xx - Configure NDISWrapper (and WPA Supplicant)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant



Now, REBOOT.

---

### Post by myharshdesigner on 2007-11-12
This is workd For me on both ubuntu 7.04 and ubuntu 7.10

Thanks

---

