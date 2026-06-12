---
title: "How to use same wireless network manager in Mepis"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by loobyloo on 2009-12-15
Hi all

First of all...if this comes across as slightly disloyal to Ubuntu and its users, then I do understand but in the wider interests of Linux promotion I'd still be grateful of any answers.

My main OS is Mepis 8.0, with a dual boot into Ubuntu.  I have endless problems connecting to the internet with Mepis: it's very erratic and unpredictable, especially at the University where I spend at least 40 hours of my week and where people expect to be able to contact me by email.  Ubuntu, OTOH, well, I can't offhand remember a single time in the 18 months I've been using it where it failed to connect first time.  This morning, for eg, Mepis is telling me I am "connected to [my Uni] at 0db." And you can't do much on 0db.

I was wondering if I could transfer the software and settings that Ubuntu uses so successfully over to Mepis in order to get it to work.  In Mepis I use wicd, which everyone recommends as being a better connection manager.  Well, I've yet to see evidence of that.

Could anyone tell me if there's a straightforward way of getting Mepis to behave in the same way when it connects as Ubuntu?  I'm using Jaunty and the kernel is 2.6.28-13-generic and I haven't, AFAICR, altered any of the default connection settings.
The wireless card (output of lspci) is Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Many thanks!

---

### Post by hansdown on 2009-12-15
Hi loobyloo.

I haven't used mepis for a while.

The mepis documenttion wiki might be helpful.

[http://www.mepis.org/docs/en/index.php/MEPIS_8_Network_Assistant](http://www.mepis.org/docs/en/index.php/MEPIS_8_Network_Assistant)

---

### Post by northern lights on 2009-12-15
First off, I have no experience using Mepis.

However, have you tried connecting to the wireless via the shell?

What happens, if you run```
dhclient wlan0
```?

---

### Post by loobyloo on 2009-12-15
> **northern lights said:**
> First off, I have no experience using Mepis.

However, have you tried connecting to the wireless via the shell?

What happens, if you run```
dhclient wlan0
```?

Hi 

it's a bit long to copy over from the other computer by hand but the last line of it before it stopped was 

No working leases in persistent database - sleeping.

Apparently I@m not the first to have this problem
[http://www.mepis.org/node/6739](http://www.mepis.org/node/6739)

Not to worry -it's really a question for Mepis forums.  Thanks so far!

---

