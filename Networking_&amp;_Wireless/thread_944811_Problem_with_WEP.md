---
title: "Problem with WEP"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by chantzzzzz on 2008-10-11
I've got some issues with my wireless networking. At university, using their wireless system which runs on a WPA enterprise system needing a more complex authentication process, my wireless works just fine. At home however, all we have is just a simple D-Link using a 128 bit WEP key. I'm positive everything is being entered in properly, and it will say it's connected. However, the internet doesn't work and after a minute or two, I will be prompted to enter in the password for my network. It isn't a huge deal, but this is quite annoying as I have to boot into XP at home if I want to get on the internet. Any help would be appreciated 

Intel Wireless WiFi Link 4965 AGN
Xubuntu 8.04 Hardy Heron

---

### Post by sh_son on 2008-10-12
Hi,

I also have Intel 4965AGN but mine connects to broadcasting/hidden wireless networks using gnome Network Manager without any issue;

Maybe, which driver are you using at the moment? I'm using '**iwl4965**'.

---

### Post by Sava8420 on 2008-10-12
> **chantzzzzz said:**
> I've got some issues with my wireless networking. At university, using their wireless system which runs on a WPA enterprise system needing a more complex authentication process, my wireless works just fine. At home however, all we have is just a simple D-Link using a 128 bit WEP key. I'm positive everything is being entered in properly, and it will say it's connected. However, the internet doesn't work and after a minute or two, I will be prompted to enter in the password for my network. It isn't a huge deal, but this is quite annoying as I have to boot into XP at home if I want to get on the internet. Any help would be appreciated 

Intel Wireless WiFi Link 4965 AGN
Xubuntu 8.04 Hardy Heron

So the best way to configure a wireless connection is manually.  To do this you need to enter the terminal then run:
```
sudo iwconfig 
```
this should show all your connections.  Should have lo,eth0 and wireless is most likely wlan0.  So for the rest I'll assume that is what it is, if not substitute what is listed for wlan0. Next:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "nameinquotes"
sudo iwconfig wlan0 key insertyourkeyhere
sudo iwconfig wlan0 key open *see below
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

*Depending if connection key is open or restricted most likely it is open if so then enter command as shown.  After running final command it should connect to link.  If you don't know the name of the network or for more specific link info. run:
```
sudo iwlist wlan0 scan
```
This will list networks in area and show details of link.  If you want to further configure network details run:
man iwconfig
It will show you all iwconfig options. To exit the manual hit the "q" key.  Good luck.

---

