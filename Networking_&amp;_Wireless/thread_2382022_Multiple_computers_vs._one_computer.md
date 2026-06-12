---
title: "Multiple computers vs. one computer"
date: 2018-01-08
forum: Networking &amp; Wireless
---

### Post by pengyou2 on 2018-01-08
This is a combination networking and hardware question. I have started to learn and practice hydroponics (HP) - I am hoping to develop it into a last (final??) career change as I swing into retirement - and want to collect and store data electronically about my system, as well as to control it.  I am leaning towards using a raspberry pi to do the data collecting and controlling on each site.  I have 3 hp sites in my home so want to consolidate my data on one server.  I also have a couple of home security cameras that I want to store data, a weather station to collect data from have and set up my browser to download pages and data during the daytime, when internet usage in my neighborhood is really low - no one is  home :)  What kind of hardware should I use?  I have a pc with an i5 that is not being used now.   Will the raspberry pi be useful?  Or is there a better/cheaper way to connect multiple sites to one computer for data collection?  Are they overkill?  My concern here is both dependability and affordability - simplicity also, but I am willing to dig into a few webpages and study if it will get me dependability at a lower price.  Right now, the computers are only 10-20 feet apart, but once I am in practice, they will be 100-300 feet apart.

---

### Post by wyliecoyoteuk on 2018-01-08
The Raspberry pis might be useful for collecting data, but Sd cards are not reliable storage, especially if it involves multiple writes.
for managing cameras, Motioneye is a nice simple interface. There is even a motioneyeOS designed for Raspberry Pis.
Zoneminder is more powerful, but also more complex.
You could also look at Opensprinkler, and OpenHab ( which is far more than a simple home automation package, it has bindings for sprinklers, wifi sockets, lighting ,cameras and weather stations, etc).
Without knowing more about the hardware, it is hard to be specific.
It sounds like you want to collect data and upload it in batches.
Nextcloud would probably be useful. I use it, for exaample the app uploads my phone photos, whenever I connect to a wifi network. It is very versatile.

Depending on the hardware and type of data, MQTT might also be useful.

---

