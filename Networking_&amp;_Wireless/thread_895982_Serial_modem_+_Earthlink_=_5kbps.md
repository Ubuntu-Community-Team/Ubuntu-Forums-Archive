---
title: "Serial modem + Earthlink = 5kbps"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-08-20
I needed to set my grandmother up with dial up (she lives out in the country) and the only serial modem I could find locally was a Zoom 56k dial up serial modem.  It works quite well and I have seen pretty good reviews online about it (at least most aren't complaints!).  Unfortunately it only connects at 5kbps!!  This is really quite maddening.  I tried many numbers and the tech simply informed me that they don't support linux on the phone.

I have never had to use a dial up modem.  I am used to the simple setup that we enjoy with dsl and other broadband options.  I believe the problem is with the init strings that gnomeppp uses.  I have no experience with, therefore no understanding of, init strings and how to even go about figuring out which ones to use.  So I have a couple questions. 

1) Are the init strings dealing with the modem or the isp?  In other words should I be looking for "earthlink init strings" or "zoom init strings?"

2) How would I go about identifying the appropriate strings?

3) (I know I said a couple) Has anyone else solved this problem and if so, how?

Thanks

JTS

---

### Post by teryret on 2008-08-21
It's important to differenciate between units when you're dealing with modems.  Baud != bits/sec and even more importantly kbps (ie kbits/sec) != kBps (kbytes/sec).  

From [wikipedia]("http://en.wikipedia.org/wiki/List_of_device_bandwidths"): 

> Modem 56k (8000/3429 baud) (V.90)	56.0/33.6 kbit/s[4]	5.6/3.36 kB/s[3]
Modem 56k (8000/8000 baud) (V.92)	56.0/48.0 kbit/s[4]	5.6/4.8 kB/s[3]

So if upon closer inspection you're really getting 5kBps instead of 5kbps then congrats, you're going at almost dial-up topspeed.  Otherwise test it in windows, I'd bet on it giving similar speeds, and if so call up the POTS and complain of a noisy line.

And I nearly forgot, the init strings are on a per-modem basis.  But as long as your init string tells your modem to auto negociate speed starting from 56k(bit/s) and you're getting a connection then the problem is probably elsewhere.

---

