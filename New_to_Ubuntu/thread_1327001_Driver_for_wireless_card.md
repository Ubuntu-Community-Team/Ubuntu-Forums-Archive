---
title: "Driver for wireless card"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by jcmven on 2009-11-15
greetings, this is my first time using Ubuntu and I installed into my laptop Lenovo 3000 N200...works fine and almost all drivers the ubuntu 9.10 version has it, but I have problems with my wireless card BROADCOM BCM94311MCG MINI CARD, where can I find this driver to download it.  thanks!!!!

---

### Post by JoeGoe on 2009-11-15
I think this is how&#65279; I fixed this
1) System-Administration-software sources
2) Select Cd-rom with ubuntu karmic koala
3) Insert the cd
4) System-Administration-Synaptic Package Manager
5) Type bcmwl-source-kernel
6) Mark for installation
7) Apply the changes
8) remove the CD
9) Reboot
10) Wireless Access Points should now be availible

I hope this helped

---

### Post by MontelEdwards on 2009-11-15
Unforutnately, I was not able to find a native Linuxs driver for this. 
There is a way that we can take the Windows driver and use it on Linux with ndiswrapper.

First open a terminal by going to Applications>Accessories>Terminal
Input..
*note: Sudo is a program that lets you have root privileges need to run some commands. When prompted for your password you will **not** see the letters being typed, but they are. Just type and enter. *
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get remove bcm43xx-fwcutter
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist.conf
```_**[COLOR=Red]Now reboot your system.[/COLOR]**_

Once back, open a terminal and:
```

wget http://montel-assist.googlecode.com/files/WLANBroadcom.tar.gz
tar -xzvf WLANBroadcom.tar.gz
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
wget http://montel-assist.googlecode.com/files/ndiswrapper-1.55.tar.gz
tar -xvzf ndiswrapper-1.55.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install
cd ~/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
echo ndiswrapper | sudo tee -a /etc/modules
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```_Reboot and pray._


[Source]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a14b8a20c3973fe959032bd1566ad35dceb30132")

---

