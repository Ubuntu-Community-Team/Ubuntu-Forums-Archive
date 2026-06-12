---
title: "Everything is disabled by hardware switch..."
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by Av3nger1 on 2014-06-11
Hello to everyone,

I'm a beginner with Ubuntu but I'm learning fast....

I have one unusual problem....laptop is Fujitsu Siemens Amilo pi 1505....my new wifi adapter (card inside laptop) Realtek RTL 8191SEvB (from ebay) is not working....it is detected but always says that "Wi-fi is disabled by hardware switch"....well, my first thought was that card is faulty...but I used it on one Toshiba laptop with Windows 7 and it worked perfectly...

Strange thing is that wi-fi card from that Toshiba was working fine on Amilo pi 1505...so we can say that hardware switch is not broken (there is a switch with off-on, not combination of keys like Fn+something)...

Since I have problem only with this laptop Amilo pi 1505...I decided to buy some wi-fi usb adapter from e-bay...it seemed to me that was easier solution, because some older wifi usb adapter worked fine on Ubuntu 12.04 but then suddenly died...well, now I can say that at least seemed to me that was easier solution...

When I connect that new wi-fi usb adapter it says that is disabled by hardware switch...same thing like wi-fi card inside laptop?!...but on Windows 7 worked fine I mean usb wifi worked fine after driver installation...Windows 7 and Ubuntu where on that laptop...not dual boot...

Ok, I know that I need to install driver for that usb wifi stick and I really hope that driver is going to fix the problem...but I can't find how to install them, I always get some kind of error whatever solution I use....on disc that I got with this wifi usb adapter is some old driver for Linux and is not working...

Using google I tracked some driver "92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz"...only problem is that I don't know how to install it...

So I'm asking you guys for help.....

I would be grateful if someone knows how to enable at least one of this two wifi adapters....

I read some forums where people are saying that stupid Fujitsu Siemens made restrictions in BIOS for hardware changes...some "blacklisted" and "whitelisted" hardware devices... I hope that is not in my case...

NOTE: This laptop is not for me, I know that is old but it's for my parents and they need it only for reading news, playing Kpatience and checking email....so you see that buying new laptop is waste of money...and I need to say that they love Ubuntu much more then Windows...that's the reason why I'm trying to enable this wifi adapters on Ubuntu...

EDIT: Now is Ubuntu 14.04 on that laptop..

---

### Post by tgalati4 on 2014-06-11
What happened to the original wireless card that came with the Amilo?

Open a terminal and post the output of:

```
rfkill list
```

It is unfortunate, but many manufacturers do put whitelist restrictions in their BIOS to "improve" security.  If you are going to issue thousands of laptops to sales employees, you don't want them swapping components because that makes IT support more difficult.  Of course, it forces the same IT staff to purchase overpriced OEM wireless cards to fix their broken machines.  How did you or your parents get the machine originally?

Before installing some random driver, we need some more information.  What version of Ubuntu are you using?  Make sure you have a working ethernet cable connection for installing new modules (drivers) because you will need it.

---

### Post by Av3nger1 on 2014-06-11
> **tgalati4 said:**
> What happened to the original wireless card that came with the Amilo?

Open a terminal and post the output of:

```
rfkill list
```

It is unfortunate, but many manufacturers do put whitelist restrictions in their BIOS to "improve" security.  If you are going to issue thousands of laptops to sales employees, you don't want them swapping components because that makes IT support more difficult.  Of course, it forces the same IT staff to purchase overpriced OEM wireless cards to fix their broken machines.  How did you or your parents get the machine originally?

Before installing some random driver, we need some more information.  What version of Ubuntu are you using?  Make sure you have a working ethernet cable connection for installing new modules (drivers) because you will need it.

Ty for answering so quickly....

Already try that with "rfkill list" and "rfkill unblock all"....."rfkill list" says that hardware is blocked....

Heh...original wifi card is missing because my old man bought that laptop for around 20$ on some local fair and he is not IT man...he thought that was a good bargain....for now it seem ok, everything is working fine, only that wifi is missing...

On Amilo pi 1505 is Ubuntu 14.04 (latest with every update).....right now is connected on ethernet cable...

---

### Post by tgalati4 on 2014-06-11
$20 is cheap for a laptop, but expensive for a doorstop.  

There are some tips on this page:  [http://www.tomshardware.com/forum/27724-43-laptop-doesn-power-wireless-card](http://www.tomshardware.com/forum/27724-43-laptop-doesn-power-wireless-card)

---

### Post by Av3nger1 on 2014-06-11
> **tgalati4 said:**
> $20 is cheap for a laptop, but expensive for a doorstop.  

There are some tips on this page:  [http://www.tomshardware.com/forum/27724-43-laptop-doesn-power-wireless-card](http://www.tomshardware.com/forum/27724-43-laptop-doesn-power-wireless-card)

Yea is cheap....probably because his look is not so attractive (scratches, missing screws, some broken palstic etc)...

Heh...already read about that on that forum...but I don't want to flash BIOS etc...done it only one time and after that I said that I won't be doing BIOS upgrades anymore....

Tried this with some 20-th pin taping...but not working...also tried to find some detailed instructions but there is none....

---

