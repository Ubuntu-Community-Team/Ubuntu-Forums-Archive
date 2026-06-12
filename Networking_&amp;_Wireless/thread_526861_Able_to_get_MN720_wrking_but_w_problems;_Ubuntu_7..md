---
title: "Able to get MN720 wrking but w/ problems; Ubuntu 7.04"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by jubane on 2007-08-16
Am using a Microsoft MN720 card. Using Synaptic Package Manager I installed ndiswrapper-utls-1.9, ndiswrapper-source, and ndiswrapper-common. I used the mn720-ankh.inf driver downloaded from the web. Driver installed ok no problems. Once done I plugged in the card and of course got no lights, so I did the commands that fixed it last time for me,

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

Once I did the last command I got all the lights and the card was working and seeing my network. 

Now the first problem that I ran into is that it will not work with WPA and WEP 128bit only with WEP 64bit :confused: 

Second problem is that once I restart the computer I loose everything. Once ubuntu is booted I have to plug in the card go to terminal do sudo modprobe ndiswrapper. Once the lights on the card are on then I can go to network settings to put in the wep 64bit code and I am finally able to surf the web.

Has anyone had these problems or know of a solution???

---

### Post by mtpkts on 2008-01-01
Does anyone know where I can download the MN720-ankh.inf driver? All the links are broke....

---

### Post by z.s.tar.gz on 2008-06-21
Go to where the download was for the original files, and there is a note about the broken links. A few lines below that are 2 new links to the files.

---

