---
title: "New Ubuntu User with another wireless question"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by cemimms on 2010-05-06
Hello this is my first post here so take it easy on me!  I did search around a bit before I got too lazy and decided to just ask in a new thread. 
 
So anyway, my RC Windows7 is getting ready to expire for good June 1 and I figured I'd give the new Ubuntu release a shot before I make a final decision on what to run as my main OS and whether or not I will buy a copy of Win7.  That said my old PC is running in the living room as a media center PC with XP and I have that box wired and the wireless router with it in the living room.  So I need to get Wireless working in my room on the Ubuntu computer or it's going to be Windows 7 come next month. 
 
My current wireless adapter is:
encore enlwi-nx2, it's an 802.11n PCI adapter
 
1) Will it work?
 
and 
2) Do you all know of any wireless adapters known to work out of the box with Ubuntu 10.04 LTS that might be easier for me to just get and forget the encore adapter I already have?
 
Again sorry for not researching more on my own but it's been a long day already.  Any help would be much appreciated.
 
Thanks,
Chris M 
 
The OS is 64 bit btw if that matters, Intel BOXDG41TY mb w/ core2 duo  4GB

---

### Post by HereInOz on 2010-05-06
I tend to go with any wireless adaptor which has an Atheros chipset.

Broadcom chipsets are still troublesome, I believe, but I could be wrong, and I understand that RALink chipsets work OK as well.

I have never had an issue with an Atheros chipset, so I tend to be conservative and stick with them.

---

### Post by HereInOz on 2010-05-06
According to a couple of posts I have just seen, there is no Linux support for the chipset on the Encore.  Seems it is a Realtek chipset.

Sorry.

---

### Post by cemimms on 2010-05-06
> **HereInOz said:**
> According to a couple of posts I have just seen, there is no Linux support for the chipset on the Encore. Seems it is a Realtek chipset.
 
Sorry.
 
Yea it is Realtek
 
so what is a good atheros adapter?  i did a quick serach and saw that some TP-Link adapters have atheros chipsets?  What brand do you recommend?

---

### Post by cemimms on 2010-05-06
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704041&cm_re=wireless_adapter-_-33-704-041-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704041&cm_re=wireless_adapter-_-33-704-041-_-Product)
 
How about this TP-LINK one?  This is atheros I belive. 
 
$14.99, thats not too bad!  I'd rather get the PCI card but thats twice the cost and my router only puts out 150Mb/s anyway.

---

### Post by HereInOz on 2010-05-06
I have used TP-Link with great success.

---

### Post by cemimms on 2010-05-06
> **HereInOz said:**
> I have used TP-Link with great success.
 
 
good to hear, I will order one of those from newegg tomorrow

---

### Post by CiscoPenguin on 2010-05-06
Netgear also uses Atheros in some of their cards.  I have it working in Backtrack 4.

Check this out [http://www.dudek.org/wireless]("http://www.dudek.org/wireless")

---

### Post by lkraemer on 2010-05-06
Will you please furnish more information?

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........

lk

---

### Post by cemimms on 2010-05-06
Thanks! (edit: not sure why the "quote" option isn't working for me)

---

### Post by cemimms on 2010-05-06
Sure, just give me a couple minutes.  I'll have to boot from my ISO dvd again as I haven't done a full install yet, I'm back on windows 7 right now

---

### Post by HereInOz on 2010-05-06
From the link in CiscoPenguin's post, you may have trouble with the TPLink USB device, but not with the PCI cards.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be  helping for other Netgear adapters. Or  You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :smile:

---

### Post by Paradoxfox93 on 2010-05-18
Have you tried Ndiswrapper with any of the windows drivers?  I'd like to know if I can buy this item.

Try this tutorial (Post #9) [http://ubuntuforums.org/showthread.php?t=571129](http://ubuntuforums.org/showthread.php?t=571129)

You should be able to skip the manual compilation by pulling 1.56 from the repo with synaptic package manager.

It would help if you could post the outpost and find the chipset so we know what windows drivers you need.

---

