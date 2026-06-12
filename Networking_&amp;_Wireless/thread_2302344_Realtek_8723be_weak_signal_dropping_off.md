---
title: "Realtek 8723be weak signal dropping off"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by lgastmans on 2015-11-09
Desperate for help. 
I have tried many options that I found in the forums but none work. 
I bought an HP laptop that has a Realtek 8723be wifi adapter, and the signal is extremely weak and if it works when sitting right next to the router, it cuts off after a short while. 
Anybody have recent info on this?
I should mention that it is a fresh install of Ubuntu 14.04
Please help someone

I have the following lines in the rtl8723be.conf file :
Options rtl8723be fwlps=N ips=N

But I wonder if they have any effect because

Modinfo rtl8723be 

Always returns the same result whether i set these params equal to. N or Y

---

### Post by jeremy31 on 2015-11-09
> **lgastmans said:**
> I have the following lines in the rtl8723be.conf file :
Options rtl8723be fwlps=N ips=N

But I wonder if they have any effect because

Modinfo rtl8723be 

Always returns the same result whether i set these params equal to. N or Y

It never changes looking at modinfo, you can check
```
for p in /sys/modules/rtl8723be/parameters/*; do echo $p; cat $p; done
```

And see what it says under fwlps.  It might help to set msi to Y
```
echo "options rtl8723be fwlps=N msi=Y" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be
```

---

### Post by lgastmans on 2015-11-10
Thank you Jeremy31

A few observations:

1. the internet connection shows now, but the signal is very weak. 

2. I bought a tp-link ethernet adapter, and with that dongle, the signal is stronger and I am able to connect. The problem is, I have installed Ubuntu 14.04 fresh, and if Irun the latest updates, then even the dongle starts giving trouble: it drops after a while.

3. I am afraid to do anything now, because at some point my dongle stopped working totally, and then I had to re-install Ubuntu again.

Any ideas?

All right - back to good ol' Windows.

All kinds of threads, all kinds of updates - nothing got the Realtek 8723be working.

Sad

---

### Post by mörgæs on 2016-01-18
> **lgastmans said:**
> The problem is, I have installed Ubuntu 14.04...

Yes, 15.10 would have been a better version.

Anyway, your decision. If you are happy with Windows then all is good.

---

### Post by lgastmans on 2016-01-18
No, not happy with Windows, but to be honest, I got frustrated because I did try a lot of different suggestions. And even though I find my way around in the terminal in Ubuntu, I am no whiz... 

I did try 15.10 and it was exactly the same problem...

I will wait for 16.04

---

### Post by mörgæs on 2016-01-18
You could also test 16.04 now and discuss the results in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). Now is a good time for raising a bug report, if necessary.

---

### Post by lgastmans on 2016-01-18
Did not think of that, I was going to wait until April :-)

Will definitely give it a try!

---

### Post by mc4man on 2016-01-18
The issue is seen in this thread, there is currently no solution other than opening the case & switching the antenna wire.
(- I've got one here on new laptop, not going to open the case, getting a usb wifi
[http://ubuntuforums.org/showthread.php?t=2304607](http://ubuntuforums.org/showthread.php?t=2304607)

tracking issue - [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)
Edit: last post by lwfinger is unclear if the driver from the mentioned branch fixes without moving antenna...

---

### Post by lgastmans on 2016-01-18
mc4man: I am interested to know whether you get it working with a usb wifi dongle, because I tried that, too. With the usb wifi dongle, the signal was strong (normal), but it would still suddenly cut off after a period of time.

I am definitely not opening the case...

---

### Post by jeremy31 on 2016-01-19
Looks like Larry Fingers latest might work

Try [http://askubuntu.com/a/722904/300665](http://askubuntu.com/a/722904/300665)
You will have to delete any existing rtlwifi_new directory in your home folder beforehand

---

### Post by lgastmans on 2016-01-19
Thanks for that jeremy31.

The laptop in question is not with me anymore, and next time I buy a laptop I will first check the hardware configuration :-)

I thank everyone in this thread for their responses, and just for the sake of it: I love Ubuntu, and been on Ubuntu for many years - this was the first time I hit a road block...

---

### Post by mc4man on 2016-02-04
> **lgastmans said:**
> mc4man: I am interested to know whether you get it working with a usb wifi dongle, because I tried that, too. With the usb wifi dongle, the signal was strong (normal), but it would still suddenly cut off after a period of time.

I am definitely not opening the case...
Just to complete - 
The git driver & setting to ant2 worked here but then exposed more crap with realtek, the connection was good for about 30 min. & then the adapter would shut down.
(still connected. Only way to get back was disconnect/reconnect

Brought the laptop elsewhere & hooked up to ethernet (also realtek), same issue, 30 mins or so then off.

So am now using the usb wifi, works perfectly, never drops or anything. Using this one - 

[http://www.amazon.com/gp/product/B00EQT0YK2?psc=1&redirect=true&ref_=oh_aui_detailpage_o04_s00](http://www.amazon.com/gp/product/B00EQT0YK2?psc=1&redirect=true&ref_=oh_aui_detailpage_o04_s00)

This is the first time I got a laptop without Intel wireless & not realtex ethernet (current good laptop has Qualcomm Atheros ethernet) & I'll Never get another laptop with the realtex network garbage

---

### Post by lgastmans on 2016-02-04
yes, I learnt my lesson, too: always check the hardware specs before buying a laptop :-)

---

