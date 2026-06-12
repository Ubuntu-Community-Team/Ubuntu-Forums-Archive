---
title: "Howto setup AR5007EG in Hardy Heron 64 Bits"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Joe Driller on 2008-05-15
PROCEDURE FOR UBUNTU HARDY HERON 64 Bits USERS

Go to System/Administration/Hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

Ensure you have your kernel headers and the build essential package. Use Synaptic or:

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

Install ndisgtk. Use Synaptic or:

sudo apt-get install ndisgtk

Get 64 Bits XP drivers from blakemartin:

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

Blacklist the default driver

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Load Ndiswrapper and XP driver:

sudo ndiswrapper -i net5211.inf

Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

sudo reboot

At this point your network card must work O.K. if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.

When you reboot your PC in most cases AR5007EG doesn’t work anymore (maybe find networks but can’t connect to them)
Victor Nieto has written a script to solve the problem but this script must be executed before X server starts, I tried this and works ok EVERY TIME YOU TURNS ON YOUR PC.

first of all here is the Script:

Use an editor and copy-paste this: (pay attention in the 1st. line in other posts looks like “#bin/bash”, correct it)

#! bin/bash
modprobe -r ndiswrapper
cp /etc/modprobe.d/blacklist .
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist

save the file as subirwifi

Copy file into /etc/init.d and change file mode

sudo cp subirwifi /etc/init.d
chmod +x subirwifi

Now we need to make a symbolic link in /etc/rc5.d to load driver before X server starts.
go to /etc/rc5.d

sudo ln -s /etc/init.d/subirwifi S09subirwifi

if all was correct you should see a line like this when you do ls -l

lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi

reboot your system and… Luck!!!

I am using this in a Compaq C735EM Laptop with Hardy Heron 64 Bits and works fine (execept blue led)

Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the Script.

---

### Post by Gotsbee on 2008-05-16
I am writing this using my newly working wireless connection.
Thanks so much for putting this together. I was just starting to get frustrated.
The comp is an Acer Aspire 7520-5839 (Canadian Model). The /etc/init.d script was essential for me. 

Thanks again!

... Now to start getting WoW working :)

---

### Post by Joe Driller on 2008-06-09
After using my laptop for many weeks I noticed that sometimes I'm still having problems with the Atheros wifi. Reading forums over the net and talking with other persons with this problem seems that the problem is ***_DEFINITIVELY SOLVED_*** I've been working with my laptop for the last 3 weeks in many different situations and the wifi works fine ***_EVERY TIME_***. I be able to connect to every wifi lan I found. The only thing you must to do is apply the method described in my last post but replacing the script with this one:


#!/bin/bash
sudo modprobe -r ndiswrapper
cp /etc/modprobe.d/blacklist .
sed 's/#blacklist ath_pci/blacklist ath_pci/g' /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
sudo ndiswrapper -r net5211
sudo ndiswrapper -i /usr/lib/ar5007eg/net5211.inf
sudo ndiswrapper -ma && sudo ndiswrapper -mi
sudo modprobe ndiswrapper
sed 's/blacklist ath_pci/#blacklist ath_pci/g' /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start




and creating the symbolic link in rc2.d instead of rc5.d



Thats all folks !!! Wi-Fi working perfectly and every time you want.

---

