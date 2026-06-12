---
title: "Can someone help me find a way to get this Windows WI-FI driver on Lubuntu?"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by criz-apy on 2015-06-03
So I decided to kick the bucket with Windows XP,too many problems have been popping up since it stopped being supported and honestly it was just time to move on. I decided to go with a Linux distro since I'm trying to save up for a gaming pc and didnt have the money to by a copy of windows so I looked it over and choose Lubuntu 12.04 it suited all my needs as I just need this pc to just cling to life a little longer. I ran into a problem after I installed Lubuntu over Windows XP and that was my favorite USB wi fi adapter wasnt compatible and I had to go back to my old one which is extremely weak and almost never connects (Im lucky this loaded) so My question is is their a work around to this? I have the install disc with all the drivers is there anything I can do?

USB wi-fi Adapter: Buffalo AC433 Dual Band Wi-Fi Adapter

---

### Post by kerry_s on 2015-06-03
plug it in while your connected & run additional drivers to look for the driver.
or
install ndisgtk & then you can use the windows drivers you have.

---

### Post by coldraven on 2015-06-04
> **kerry_s said:**
> plug it in while your connected & run additional drivers to look for the driver.
or
install ndisgtk & then you can use the windows drivers you have.

I think kerry_s meant to say connect your laptop with a network cable then plug in the wifi adaptor. Then press the Winkey (also known as the Super key) and start typing "additional". The Additional Drivers icon will appear, click that and let it search. 

Another method is to buy a new wifi dongle, they are cheap at about $6 or less and will use the faster "n" protocol.

[http://www.ebay.co.uk/itm/MINI-WIFI-USB-WIRELESS-ADAPTER-DONGLE-150MBPS-LAN-NETWORK-RASPBERRY-PI-2-RT5370/231483794170?_trksid=p2047675.c100011.m1850&_trkparms=aid%3D222007%26algo%3DSIC.MBE%26ao%3D1%26asc%3D20140107083358%26meid%3D8ada3959ce7746b3a87d1f6f03b875b7%26pid%3D100011%26rk%3D1%26rkt%3D10%26mehot%3Dpp%26sd%3D261248547242](http://www.ebay.co.uk/itm/MINI-WIFI-USB-WIRELESS-ADAPTER-DONGLE-150MBPS-LAN-NETWORK-RASPBERRY-PI-2-RT5370/231483794170?_trksid=p2047675.c100011.m1850&_trkparms=aid%3D222007%26algo%3DSIC.MBE%26ao%3D1%26asc%3D20140107083358%26meid%3D8ada3959ce7746b3a87d1f6f03b875b7%26pid%3D100011%26rk%3D1%26rkt%3D10%26mehot%3Dpp%26sd%3D261248547242)

---

### Post by Bucky Ball on 2015-06-04
AVOID ndiswrapper (ndisgtk) at all costs and only treat as a last resort. Ndiswrapper is largely superseded and has been replaced by B43, STA and others. Try coldraven's instructions first, and also, plug it in and run these two commands:

```
sudo lshw -C network
lsusb
```

... hitting enter after each. Post the output here between [code] tags, thanks (see the last link in my signature for how).

---

### Post by criz-apy on 2015-06-04
Thanks for all your ideas ill try them

---

### Post by criz-apy on 2015-06-07
So far ive been having no luck do you think  I could use wine to install it?

---

### Post by jeremy31 on 2015-06-07
Bucky Ball wants you to run the commands  in terminal and post the output and look at the link in Bucky's post about using code tags to paste the terminal output in- it keeps the formatting and prevents info from turning into smilies

---

### Post by Bucky Ball on 2015-06-07
> **jeremy31 said:**
> Bucky Ball wants you to run the commands  in terminal and post the output and look at the link in Bucky's post about using code tags to paste the terminal output in- it keeps the formatting and prevents info from turning into smilies

^^^
This. Try our suggestions and post back your results. Wine is not the way to go. Ndiswrapper is designed for Win wireless drivers, but we have no idea if you need one of those until you post your output. ;)

Unlike Windows, there are lots of drivers already present in the Ubuntu kernel and workarounds to install them if they're not (99% of the time). Your output will tell us what your card is, what state it's in and what driver, if any, it is using.

---

### Post by criz-apy on 2015-06-07
Oh ok

---

