---
title: "E220 usb modem"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by djdan00 on 2008-05-01
Im new to ubuntu and have 8.04 finally got the vodafone drivers working with my Huawei E220 but are having problems with DNS (new beta drivers).
It comes up with DNS error and says its not being assigned an IP either.
Im on 3 UK and have username and password of web.
It should assign IP and DNS automaticly.

Any ideas or same problems??

Thanks

---

### Post by juntima on 2008-05-01
I'm sorry I can't answer your q, I havent even got that far with my E220 How did you get Ubuntu to recognise the dongle? I had it up and running on Xandros but no luck with Ubuntu

---

### Post by pseudo-random on 2008-05-01
[http://wintolin.co.uk/content.php?c=tuts/e220](http://wintolin.co.uk/content.php?c=tuts/e220)

---

### Post by daka on 2008-05-03
Hi

I am having problems also with Vodafone Mobile Connect card... much more problematic in Heron ... needing to do the following:

modprobe usbserial vendor=0x12d1 product=0x1003
then disconnecting and reconnecting the modem
then
sudo modprobe -r ehci_hcd

before Huawei E220 will initialize

Anyone else experiencing these problems with modem being recognized... who maybe has a better fix for the problem?

Daka

---

### Post by MattBD on 2008-05-03
I briefly had a Vodafone Mobile Connect card, but took it back because the performance was terrible where I live.
Vodafone have [a website where you can download a driver for their Huawei cards]("https://forge.vodafonebetavine.net/frs/?group_id=12"), including a deb package that worked fine with Gutsy and I guess should be OK with Hardy too. Be warned, it has more than a few dependencies, so you'll need another way to connect to the Internet to get it working.
Once it's installed, if you start the driver from the menu, the settings you need are "internet" for the APN and "web" for the user name and password.

---

### Post by MattBD on 2008-05-03
> **djdan00 said:**
> Im new to ubuntu and have 8.04 finally got the vodafone drivers working with my Huawei E220 but are having problems with DNS (new beta drivers).
It comes up with DNS error and says its not being assigned an IP either.
Im on 3 UK and have username and password of web.
It should assign IP and DNS automaticly.

Any ideas or same problems??

Thanks

I used [OpenDNS]("http://www.opendns.com/") and that worked fine with that.

---

### Post by dastasha on 2008-05-04
Same problem as you here daka. Unfortunately I have no solution other than returning to 7.10 where the modem and VMC works well.
I tried your workaround with no success, I probably did something wrong. Cut and pasted the commands with no success.

I will say that under 8.04 once I resolved all the dependency issues, VMC initialised and I had a succesful internet connection the first time I ran the program only. After that VMC freezes for me at the loading screen every time.

I look forward and will be watching the forums for a solution to our problem.
Will be keeping an eye on the vodafone betavine help forum also.

-Darren

---

### Post by orawax on 2008-05-07
zap.

---

