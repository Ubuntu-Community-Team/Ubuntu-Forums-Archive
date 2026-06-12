---
title: "BCM4318 Installation Solution"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by page1ink. on 2007-01-23
I've got an Acer Aspire 5100-3853 and I've been trying for three or four days to try to get the (apparently) infamous integrated Broadcom 4318 Airforce One card to work. I tried many of the tutorials on the forums and on other websites, but none of them worked for me. I finally found [this guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29") in the ndiswrapper wiki, and it worked! Make sure you download the driver from the [list on the site]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B") (for this particular laptop, it was number 63). You can compare your particular BCM card to one in the list by opening a terminal window (Applications>>Accessories>>Terminal) and entering:
```
lspci | grep Broadcom
```
My result is:
```
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
You want to search by the PCI/USB ID, which is the first set of numbers you see above (in this case, search for **06:02.0**, you can omit the 0000:). Download and extract that driver (using Archive Manager if you need to) and follow the instructions on the first link I provided. I downloaded and compiled the source of ndiswrapper instead of letting Synaptic do the work for me. I don't know if this affected anything or not.

You should be up and running in no time!

 If you use WEP, you must download NetworkManager. You can do this via Synaptic or by entering the following in a terminal:
```
sudo apt-get install network-manager-gnome
```
Then open your interface configurator (System>>Administration>>Networking). Make sure the device is active, then click on Properties and enter the necessary information. I used **iwconfig**, but it should work just fine through the configurator.

As far as WPA goes, I can't offer any advice, but the installation link above has some information on it.

I hope this helps anyone who is having issues. Good luck!

res:
Installation Guide: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29)
Driver List: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by rmartz on 2007-01-23
I also installed Wifi-radar from the Synaptic Manager. It works really easily with my 4318 allowing me to set it up for multiple networks.

---

### Post by page1ink. on 2007-01-24
I installed Wifi radar before I took the laptop out of the house and it worked flawlessly! Glad I read your reply before I drove off =)

---

### Post by rmartz on 2007-01-24
Glad it helped. My Wireless seemed to crash overnight. I am just starting to figure out what I need to do to correct it. I have a dual boot laptop, so I have to read up in XP, then reboot into Ubuntu and try to see if I can get things working. I am about to reboot. Hope I got the info I needed.

Peace.

---

### Post by rmartz on 2007-01-24
Fixed! I now have Wifi in Ubuntu again!!

Well, I will have to reboot and see if it stays fixed. :)

---

