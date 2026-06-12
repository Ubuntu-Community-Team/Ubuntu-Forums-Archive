---
title: "Raconfig utitlity for RT2500?"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by scottylans on 2005-08-09
I am following the howto - but I can't get the raconfig to work.
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

(Step 6, part 2 - RA config)

> 
6. In the Terminal, type:

sudo ./path/to/RaConfig2500

You can also run RaConfig by double-clicking on it, from either a root Nautilus or Konqueror window (sudo nautilus, sudo konqueror). 


root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys # sudo ./path/to/RaConfig2500
**sudo: ./path/to/RaConfig2500: command not found**
root@scott:/home/scott/rt2500-cvs-2005080902/Utilitys #


Any idea's? - the card looks like it's working - but according to the howto, I need raconfig for WPA?)

---

### Post by scottylans on 2005-08-09
Ok never mind I found the configuration utility and set up all the options.
It did not work and did not give me an ip

I re-booted and low and behold it works - awesome - that rt2500 howto is no where near as good as luca's ipw2200 howto - which is really catered to newbies - but I've learnt a lot fiddling with his how to - which helped me with this one.


shame my gigabyte wpkg pci card has LESS arial strength than my laptop! - i was expecting more :( - but it's unscrewable? - maybe it's an industry standard and i can pop on another arial?

(wanna sniff packets :)   )

---

### Post by danielhaden on 2005-08-10
That's a very powerful card.  Problem is that the antenna is down behind the computer.  

The Hawking corner reflect model is proven effective with this card.  It is highly directional and this helps you "punch through" interferance.  The cord itself is helpful in positioning the antenna to a place not down behind the computer.  Top of the monitor back is good if you have a CRT and some velcro sticky squares (or scotch tape).   
[http://www.newegg.com/Product/Product.asp?Item=N82E16833164110](http://www.newegg.com/Product/Product.asp?Item=N82E16833164110)

Here's an outdoor design that is fun to combine with a TV antenna rotator attachment:  
[http://www.pacwireless.com/products/DC24.shtml](http://www.pacwireless.com/products/DC24.shtml)
and
[http://www.pacwireless.com/products/vagi_series.shtml](http://www.pacwireless.com/products/vagi_series.shtml)
The vagi has high NLOS performance.  
and 
the following 11 inch antenna makes for a good antenna on its own or as a feedhorn for a recycled larger dish (if you want 83+ km range) 
[http://www.pacwireless.com/products/echo_series.shtml](http://www.pacwireless.com/products/echo_series.shtml)
I'm going to try that one on my extra 12 foot dish.  Packet huffing? ;)  
For reference, an old 3, 4 or 5 foot cheapskate sat dish can be made brilliant again by a trip to the car wash and Krylon Fusion paint plus an economy clear coat.

See also netstumbler.org

---

### Post by scottylans on 2006-06-19
[QUOTE=danielhaden]That's a very powerful card.  Problem is that the antenna is down behind the computer.  

The Hawking corner reflect model is proven effective with this card.  It is highly directional and this helps you "punch through" interferance.  The cord itself is helpful in positioning the antenna to a place not down behind the computer.  Top of the monitor back is good if you have a CRT and some velcro sticky squares (or scotch tape).   
[http://www.newegg.com/Product/Product.asp?Item=N82E16833164110](http://www.newegg.com/Product/Product.asp?Item=N82E16833164110)

Here's an outdoor design that is fun to combine with a TV antenna rotator attachment:  
[http://www.pacwireless.com/products/DC24.shtml](http://www.pacwireless.com/products/DC24.shtml)
and
[http://www.pacwireless.com/products/vagi_series.shtml](http://www.pacwireless.com/products/vagi_series.shtml)
The vagi has high NLOS performance.  
and 
the following 11 inch antenna makes for a good antenna on its own or as a feedhorn for a recycled larger dish (if you want 83+ km range) 
[http://www.pacwireless.com/products/echo_series.shtml](http://www.pacwireless.com/products/echo_series.shtml)
I'm going to try that one on my extra 12 foot dish.  Packet huffing? ;)  
For reference, an old 3, 4 or 5 foot cheapskate sat dish can be made brilliant again by a trip to the car wash and Krylon Fusion paint plus an economy clear coat.

See also netstumbler.org[/QUOTE]


Thanks heaps for your response, unfortunately UB forums didn't email me when you replied so I went off info elsewhere :/


I picked up this suckah
[http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&rd=1&item=5875500336&ssPageName=STRK:MEWN:IT](http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&rd=1&item=5875500336&ssPageName=STRK:MEWN:IT)

It looks ok, I mailed other people who bought it who seemed happy with it.

I quite like the card - the RT2500 PCI but yeah signal is GHASTLY! :(

Fingers crossed this makes it far better.

---

