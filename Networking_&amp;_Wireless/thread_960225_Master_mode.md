---
title: "Master mode"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Sanix on 2008-10-27
Hi,
I've got the following wireless card:
Intel Corporation Wireless WiFi Link 5100

It's a pretty new one, so I hope I supports the master mode. But when I try to execute the following command:

> 
daniel@daniel-hp:~$ sudo iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.


Ubuntu also created an interface called wmaster0 but there I can't set anything. I'm using Ubuntu 8.10.

---

### Post by velmont on 2009-02-08
I also wonder about this.

I want to let my girlfriend get internet on her Mac when I'm occupying her internet cable. So I want to NAT  wlan0 => eth0  on my computer. I've done this many times before with other cards...

Haven't found anything interesting about it on the web.

---

### Post by velmont on 2009-02-08
Actually, I found something useful on [https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

They say the driver we're using (iwlagn AFAIK) at least is supposed to handle it. 

> Intel PRO/Wireless (ipwXXXX) series

For ipw2100/ipw2200, unfortunately there is no way to use them as AP, but this can be done for ipw3945 and ipw4965, maybe ipw2915 too, which are pretty good cards anyway, using fully open-source iwlwifi drivers, but it can't be done with old Intel drivers with closed microcode. 

Should maybe read the README from that project. But I need to sleep now.

---

### Post by cduguet on 2010-06-23
I also have a 5100, and as I found, we don't have any opportunity for now to have master mode:

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1585](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1585)

I really hope I'm wrong, and that somebody will correct me about this. 
The modes I can get with my card I can find them with:

iw phy phy0 info

It's a shame, that this card doesn't work as AP in Linux, while in Win7 it actually works with Connectify.

---

### Post by prab97 on 2010-11-06
Bump!!!

I have the same card. Did anyone discover any way to get master mode up and running on this card?
I need to use Connectify-On-Windoze7 type functionality so that my Android device(it can't connect to ad-hoc networks) can access my wired broadband.

---

### Post by ramilehti on 2011-06-06
BUMPITY BUMP!!

Still not solved in 2011.

---

### Post by sohelmk on 2012-03-27
BUMP!!
same issue in 2012

---

### Post by RyanRahl on 2012-03-27
enter the command:

```
iw list
```

and it will tell you what modes your device supports

---

