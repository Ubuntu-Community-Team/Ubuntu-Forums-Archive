---
title: "list of networks gone"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Sepp1 on 2007-01-25
After half a year, with dapper(my first linux), I upgraded to edgy a couple of days ago. The upgrade went smoothly, but there is no longer a list of available wireless networks, when i try changing it. It is my laptop, and i use it both at home, and et school, so this is a rather serious issue. Initially it worked flawlessly with my home network. I then took it to school, but the list of available wireless networks, was not there, then i tried to type the network in maually, and now neither my home network, nor my scholl network works.

Has anybody encoutered this problem too?

This is the first problem, i havn´t  been able to look up directly, in the forums, so thanks in advance.

Sepp

---

### Post by /carlito on 2007-01-25
Have you tried to install wifi-radar? You should be able to configure your wireless network with this app. 

```
sudo apt-get install wifi-radar
```

---

### Post by Sepp1 on 2007-01-25
That helped. I can see available networks now.
Thanks

---

### Post by Sepp1 on 2007-01-28
Well now I use wifi-radar, I can see the networks in range, but nothing i have done so far has forced edgy to connect to the internet.
When i press "edit" nothing happens. It says that i am connected to my network, but nothing happens either, when i press "disconnect".
As i wrote, everything worked smooth and perfect in dapper, so I really doubt it is a hardware issue.

By the way. if all else fails; Is there an easy way of downgrading to dapper, without installing from blank?

Thanks in advance
Sepp

---

### Post by PvSinNL on 2007-01-28
Did you try iwconfig? Something along the lines of:
```
sudo iwconfig eth0 essid [ssid]
```
(You'd have to replace eth0 with the name of the wireless interface you're using, and [ssid] with the SSID of the network in question, obviously.)

This has helped me to "wake up" NM if it didn't readily associate with a particular network. This was on Dapper, though...

---

### Post by Sepp1 on 2007-01-28
It says "wiconfig command not found". should there be clamps around the networkname?

EDIT: ah IWconfig...my bad

---

### Post by Sepp1 on 2007-01-28
Hmm. that did nothing except now it says eth1 is turned off.
However wifi-radar still persists that im connected.

Thanks anyway though
sepp

---

### Post by Sepp1 on 2007-01-28
Yipii. Im on the net again. I changed the wep-encrypion from 64 bit to 128 bit, and now i am able to type the network in manually. I still dont get a list of them without wifi-radar though.
Now thats something ill work on later,

Thanks all for your help. It has really opened my eyes to what support is.
In the good old days, somebody would probably have told me to reinstall windows.

Sepp

---

