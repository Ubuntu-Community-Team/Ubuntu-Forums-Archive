---
title: "Looking for a decent USB Wireless adapter. . ."
date: 2011-05-03
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-05-03
Hi! I'm looking for a decent USB wireless adapter. Nothing too fancy, I just need it to work out of the box on Ubuntu 11.04, so kernel 2.6.38. Any suggestions?

Thanks in advance!

---

### Post by ubudog on 2011-05-04
I have this one, and I used to use it on my old 10.10 laptop.  Worked out of the box fine.  It should work fine on 11.04.  :-)

NOTE: It doesn't work (out of the box) on 10.04, and I assume on anything lower than 10.10.

[http://www.amazon.com/D-Link-DWA-125-150Mbps-Wireless-Adapter/dp/B002KEA8OM/ref=sr_1_3?s=electronics&ie=UTF8&qid=1304489003&sr=1-3](http://www.amazon.com/D-Link-DWA-125-150Mbps-Wireless-Adapter/dp/B002KEA8OM/ref=sr_1_3?s=electronics&ie=UTF8&qid=1304489003&sr=1-3)

---

### Post by wolfen69 on 2011-05-04
[This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017") usb wifi works perfect out of the box on 11.04

---

### Post by pi.boy.travis on 2011-05-04
Thanks guys, just what I was looking for!

---

### Post by satanselbow on 2011-05-04
Avoiding anything BROADCOM based should be pretty hassle free ;)

ATHEROS is also pretty well supported

You will have to look at the smallprint though as D-LINK / NETGEAR etc are the badge on the box not the chips inside ;)

---

### Post by ubudog on 2011-05-04
Yep I have had TERRIBLE experiences with Broadcom from 9.10 and below.  64 hours to get it working.  (I timed it)

---

### Post by pi.boy.travis on 2011-05-04
> **ubudog said:**
> I have this one, and I used to use it on my old 10.10 laptop.  Worked out of the box fine.  It should work fine on 11.04.  :-)

NOTE: It doesn't work (out of the box) on 10.04, and I assume on anything lower than 10.10.

[http://www.amazon.com/D-Link-DWA-125-150Mbps-Wireless-Adapter/dp/B002KEA8OM/ref=sr_1_3?s=electronics&ie=UTF8&qid=1304489003&sr=1-3](http://www.amazon.com/D-Link-DWA-125-150Mbps-Wireless-Adapter/dp/B002KEA8OM/ref=sr_1_3?s=electronics&ie=UTF8&qid=1304489003&sr=1-3)

Just ordered this from Newegg. Thanks again!

---

### Post by ubudog on 2011-05-05
No problem.  :-)

---

### Post by pi.boy.travis on 2011-05-07
Got the adapter. For anyone who reads this later, it works perfectly out of the box on 
Ubuntu 11.04. My only complaint is that it fails after a few minutes under extremely heavy load, in my case an sftp transfer at 4-6 MB/sec. I believe that it's due to heat, my infrared thermometer measured the outside of the adapter to be 129 Fahrenheit. Simply limit the buffer size of any large and fast file transfer so the rate stays at about 2 MB/sec, or carry the machine to the router and use good ole' CAT5 :P

---

### Post by beew on 2011-05-07
[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

This one works out of the box for 10.04, 10.10 and 11.04. Plug in and connect immediately(in Windows you have to install drivers). I got one for about $15.

---

### Post by pi.boy.travis on 2011-05-07
Hold on a second, I think I found out why this wireless adapter misbehaves under high load, take a look at this:

```
lsmod | grep -e rt2 -e rt3
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211

```

Looks to me like more than one module is trying to control the device!!!

---

### Post by pi.boy.travis on 2011-05-07
> **pi.boy.travis said:**
> Hold on a second, I think I found out why this wireless adapter misbehaves under high load, take a look at this:

```
lsmod | grep -e rt2 -e rt3
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211

```

Looks to me like more than one module is trying to control the device!!!

For the searchers, here's how I just solved this. Use your text editor of choice to edit this file, I prefer nano:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Go to the bottom of the line, and add this:

```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```

Save the file and reboot. Then run this to make sure the unwanted modules aren't running:

```
lsmod | grep -e rt2 -e rt3
```

You should see this:

```
rt2870sta             450556  1 
crc_ccitt              12667  1 rt2870sta

```

And your adapter should run at full speed, and not overheat under high load!

---

### Post by walt.smith1960 on 2011-05-08
For N150 speeds, my Negear WNA1100 is plug & play in 11.04.  I used Vagrale13's ath9k installer .deb package found on sourceforge for 10.04 & 10.10.

---

### Post by cotcot on 2011-05-08
I bought a TP-LINK TL-WN727N a month ago after a search for ubuntu-compatible sticks.

Works out-of-the-box with my laptop and ubuntu 10.10. 

The range is good.

---

