---
title: "Ubuntu Dialup Modem Driver?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by psychtor on 2009-02-07
Once I install Ubuntu 8.10 Desktop Edition is there anything special I need to do to connect to dial up internet using this modem?:

AT&T/Lucent L56xMF Modem
Device ID: 11C1-0440
Hardware ID: WDM_Modem/Lucent_WDM_DSVD
Driver Provider: LT (I assume that's Lucent Technologies)

I have the MDMLCNT.INF from Windows but don't know if Ubuntu has a Linux version of that.

Also, will Sun Java run on the 8.10 Desktop Edition?

---

### Post by gettinoriginal on 2009-02-07
I don't have dial up, but hope this helps:  :p
Modem Dial Up Setup
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by ModelM on 2009-02-07
Since this is not a hardware modem, you'll need a driver for it. I can't tell you where to find one, but in your searching watch for the word "mars".

At least some of the Lucent chipsets are named after planets (I have an old modem with a Lucent "Venus" chipset around here somewhere). Yours is, I believe, a Lucent "Mars" chipset. This info might be helpful in your qwest.

---

### Post by HotShotDJ on 2009-02-07
> **psychtor said:**
> Also, will Sun Java run on the 8.10 Desktop Edition?Yes.  Open Applications --> Add/Remove... and install Ubuntu restricted extras for a whole bunch of goodies, including the latest Sun Java.  Or, you could simply install Sun Java Runtime if you don't want all the other stuff.

---

### Post by lkraemer on 2009-02-07
The easy way to go it is to use an External USR Hardware Modem
with your serial port, or with a USB to Serial converter.  You
can be up and running in just a few minutes, versus trying to
find drivers, get them installed, then get the modem configured
properly.

wvdial is already included in Ubuntu for your testing & surfing.

[http://ubuntuforums.org/showthread.php?t=1036317](http://ubuntuforums.org/showthread.php?t=1036317)
4th post down the page.

lkraemer

---

### Post by the.phantom on 2009-02-08
> The easy way to go it is to use an External USR Hardware Modem
with your serial port
i agree as i spent many years on dialup

when i installed my first ubuntu i spent days pulling my hair out
and finally went to a store and got a "best data56K external modem" for serial port. the box even said it worked with linux!
came home and got online in less than 1 hour !
i was using kppp back then

---

### Post by psychtor on 2009-02-11
> **ModelM said:**
> Since this is not a hardware modem, you'll need a driver for it. I can't tell you where to find one, but in your searching watch for the word "mars".

At least some of the Lucent chipsets are named after planets (I have an old modem with a Lucent "Venus" chipset around here somewhere). Yours is, I believe, a Lucent "Mars" chipset. This info might be helpful in your qwest.

It is a hardware modem, goes in the PCI slot.

---

### Post by psychtor on 2009-02-11
> **the.phantom said:**
> i agree as i spent many years on dialup

when i installed my first ubuntu i spent days pulling my hair out
and finally went to a store and got a "best data56K external modem" for serial port. the box even said it worked with linux!
came home and got online in less than 1 hour !
i was using kppp back then

Can you mention which store? There are no computer related resources around here unless is off the shelf at Wal Mart.

---

### Post by halitech on 2009-02-11
> **psychtor said:**
> It is a hardware modem, goes in the PCI slot.

when people talk about hardware or software modems, they aren't talking about the physical device, they are talking about if the modem does the work (hardware modem) or software controls everything (software modem). the majority of the modems out today that are PCI cards are also called Win Modems because you basically have to have windows installed in order to run the software that controls them.

---

### Post by psychtor on 2009-02-11
I looked around Wal Marts website and no mention of any external modems working with Linux.

---

### Post by halitech on 2009-02-11
typically most hardware won't say it supports linux (almost taboo so they don't get in trouble with MS) but any external modem will be a hardware modem so should work

---

### Post by ModelM on 2009-02-11
Either [_this one](http://www.walmart.com/catalog/product.do?product_id=10073738)_ or [_this one](http://www.walmart.com/catalog/product.do?product_id=2017763)_ would work perfectly under Ubuntu 8.10.

---

### Post by lkraemer on 2009-02-12
If you don't have a serial port, or want to use a USB port check out
the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

Basically you will need to do the following:
Configure wvdial with:

sudo wvdialconf

the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf

Open a Terminal window (you will leave it open the total time
you will be connected via dialup)

dial out with:
$ wvdial

SURF!!!
You can go back to the open terminal window and do a CNTRL C
to terminate the connection/session, then close the terminal window.

lkraemer

---

### Post by stalkingwolf on 2009-02-12
a few months ago I set up 2 laptops for dialup. as I recall both
were Diamond Supra's.  One might of been a zoom.  anyway one was serial
the other was USB.  Both worked fine.  It took about 15 min. to have both connected. I used Gnome PPP.

One of them I got on EBAY for about 12.00, the other from craigslist for
about 7.00 ( what ever the shipping was.)

---

### Post by Oceola on 2009-02-16
Some what resolved regular dial up access for the 5610B following the wvdial suggestions.
Used the "sudo wvdialconf" command then edited the wvdial.conf with the proper user name, phone number and password.
However it bypasses something or the connection is buggy as it only uses the Dynamic and not Static.

Anyone know if it's possible to create a wvdial account using pppconfig so I can set some of the other parameters like "debug" and "static"

Thanks lkraemer

---

