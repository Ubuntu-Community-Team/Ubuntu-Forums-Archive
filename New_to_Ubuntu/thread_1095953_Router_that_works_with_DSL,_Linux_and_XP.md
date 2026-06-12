---
title: "Router that works with DSL, Linux and XP"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by aak_king on 2009-03-14
I have a Hardy Heron desktop and an XP laptop. I want to network both and connect to a DSL line. Can anyone recommend a reliable home based wireless router to work with both. I've tried Linksys and Netgear with limited success

---

### Post by supersonicdarky on 2009-03-14
Get a router that supports [dd-wrt](http://www.dd-wrt.com/dd-wrtv3/index.php) or [openwrt](http://openwrt.org/).

---

### Post by ugm6hr on 2009-03-14
> **aak_king said:**
> I've tried Linksys and Netgear with limited success

How come?

Any ADSL modem-router will do what you want.

I currently have a Dynamode, but have used various Linksys, Toshiba and Dlink routers with equal success over the years.

---

### Post by aak_king on 2009-03-14
Good question. Netgear tech support told me that they do not support the Linux platform!?!? I believe the Linksys I tried was just defective. I bought a Zoom but read the reviews online and it was generaly panned so I took it back. Before I make another purchase I just want to not waste time buying a product that is not sufficient.

---

### Post by lovinglinux on 2009-03-14
I have Linksys and it works great.

---

### Post by Jose Catre-Vandis on 2009-03-14
As long as you are connecting via ethernet and not usb, most modem-routers will work fine, as they are configured via an http interface.

Netgear may say that, but their router runs linux!

---

### Post by ugm6hr on 2009-03-14
For home use, I have found any router will do.

The web interface and connection speed / reliability is the only thing that separates them. I have found all modern routers to be up to the job I ask of them; my advice is to buy whatever is cheapest.

As mentioned, Netgear (and any other) router will work just fine with Linux, whether it is officially supported or not.

---

### Post by Captain_tux on 2009-03-14
> **aak_king said:**
> Good question. Netgear tech support told me that they do not support the Linux platform!?!?

That's laughable.

I found my Netgear router to be more solid and reliable (i.e., no signal drops) once I made the switch to Ubuntu. Using Vista, the signal would drop 5 to 6 times a day and I'd have to manually reboot the bugger... not the case with Ubuntu.

---

### Post by anewguy on 2009-03-14
If you have a basic understanding of what a router does, that being it broadcasts the packets coming in and sends the packets that need to go out, it is OS independent.  Most, if not all, of todays home routers let you either physically connect with a cable or use http to something like 192.168.1.0 or 192.168.1.1 to get to the "service" port with a browser (again OS independent) so you can configure the router.

I have used linksys, netgear and dlink routers with my Linux equipment over the years with no problems.

The bottom line is to just buy what you want.  Sometimes the cheapest isn' always the best idea as sometimes the wireless signals are weaker or noisier, but I have bought the cheapest I could get locally and never had any problems.

Don't worry about what OS you are running.

Dave :)

---

### Post by markbuntu on 2009-03-14
I have a belkin wireless router, the cheapest one I could find. It works just fine.

---

### Post by txcrackers on 2009-03-15
The first thing to remember is that the "installation software" for most DSL modems and any router is pretty much bunk - they're designed to be accessed through a browser, as well. Sometimes this information is buried, but 192.168.1.1 is always a safe bet.

I don't have **any** Windows OS's and 4 computers (desktop, DVR, laptop, netbook) with Quest DSL. I just replaced my 6-year old Netgear with a newer Linksys - and immediately flashed it with Tomato*. Rocks!

*Make sure you have a compatible router before you attempt this! (But it really is easy.)

---

### Post by 3rdalbum on 2009-03-15
If you still have the Netgear, just plug it into your computer's Ethernet port, boot up and in your web browser access the URL: [http://192.168.0.1](http://192.168.0.1)

---

### Post by teamcoltra on 2009-03-15
Yeah pretty much any router should work... the thing is they will not "support it" because there are just SOO many different types of linux it would not be nearly cost effective for them to employ different people for each type, not to mention that linux people are probably >2% of their market, and of those most of us are pretty self reliant. 

I have a belkin, but I am thinking of upgrading to a nice new router that will support tomato :)

---

### Post by ramjet_1953 on 2009-03-15
I bought a cheap SMC wireless router to plug into my ADSL router and had it up and running in just a few minutes.

Like has been said in previous posts, routers are OS independent.

Regards,
Roger :D

---

