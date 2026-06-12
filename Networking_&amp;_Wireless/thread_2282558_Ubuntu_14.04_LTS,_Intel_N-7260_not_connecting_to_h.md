---
title: "Ubuntu 14.04 LTS, Intel N-7260 not connecting to home wifi"
date: 2015-06-15
forum: Networking &amp; Wireless
---

### Post by Franois_Poyer on 2015-06-15
Hi all,

Sorry to bother you, but I've been spending hours trying to fix this, and it seems I won't be able to do this on my own so...

I'm using Ubuntu 14.04LTS (updating to a non LTS is sadly not an option) on my CLEVO laptop, with an Intel N-7260 wifi device. It usually works well, though I sometimes have to turn wifi off and on again to connect to some networks. 

But today, I tried everything I could without any luck. My laptop won't connect to my home wifi ("Freebox-5ECBD0"), while both my desktop computer (running windows 7) and my smartphone (Android 4.1) connected without a hiccup...
This happened to me last year, roughly same time of the year, and I remember spending more than a week, trying everything I found to make it work (and somehow it worked at one point, though I can't tell what fixed it). I'm telling this in case you find anything strange/non-default in the attached wireless-info file (and if that might be the cause of today's problem, please tell me how to "get back" to default...)

Thanks again for your time and kind help.

[Edit]: after founding this article [https://erickranich.wordpress.com/2014/01/21/installation-du-wifi-intel-7260-sous-ubuntu/](https://erickranich.wordpress.com/2014/01/21/installation-du-wifi-intel-7260-sous-ubuntu/) , I tried
sudo /sbin/iwconfig wlan0 power off
and tried connecting again... and it worked! I don't know how long it'll work nor exactly what I did though, so any explanation/help is still welcome! [/Edit]

---

