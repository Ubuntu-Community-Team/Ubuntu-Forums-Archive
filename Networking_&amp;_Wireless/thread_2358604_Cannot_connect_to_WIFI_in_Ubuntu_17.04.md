---
title: "Cannot connect to WIFI in Ubuntu 17.04"
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by chxxvi on 2017-04-15
I have upgraded my desktop from 16.10 to 17.04 and then i cannot successfully connect to my home's Wifi router nor other mobile phone's tethering. The usb tethering doesn't work as well.

I wonder if i did something wrong of upgrade so i created usb boot disk of both 17.04 and 16.10 for test.

Unfortunately i got the same result on the live-boot 17.04 with several tries while 16.10 got no problems at all.

I am using a usb wifi adapter: TP-Link TL-WN721N 150Mbps Wireless Lite N USB Adapter

Is it i need to downgrade to 16.10 or any solution to solve this?
Thanks for help!

---

### Post by maurizio-firmani on 2017-04-15
Try what's reported [here]("https://ubuntuforums.org/showthread.php?t=2358532&p=13633206#post13633206"); it seems some USB WLAN adapters have problems with new kernel settings; I've got my TP-LINK USB stick based on AR9271 working after doing that.

---

### Post by chxxvi on 2017-04-15
Thanks [**[COLOR=#000000]maurizio-firmani[/COLOR]**]("https://ubuntuforums.org/member.php?u=2064642"). It works now!

---

### Post by chili555 on 2017-04-15
Please see post #24 here. I suggest that you try this first before we proceed further. If you need step-by-step instructions, post back and I'll be happy to assist.

---

### Post by maurizio-firmani on 2017-04-15
Thanks chili555, it's the same solution!

---

### Post by chili555 on 2017-04-15
> **maurizio-firmani said:**
> Thanks chili555, it's the same solution!Arrgghhh! Sorry I missed your post, my friend. And I'm sorry I missed that it was solved. I suppose that the posts crossed.

In any event, we're glad it's working and I'm going to clean my glasses now.

---

### Post by chxxvi on 2017-04-15
@Chili555
Just found out how to mark the thread solved; thanks for your friendly help too :D

---

