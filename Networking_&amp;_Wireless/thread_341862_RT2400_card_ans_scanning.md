---
title: "RT2400 card ans scanning"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by macozz on 2007-01-19
Hi all,
I have a Toshiba Satellite laptop with a PCMCIA APC wireless card with RT2400 chipset. It worked fine and cleanly with Dapper, using RT2400 driver and the RaConfig2400 utility to scan access points. As far as I remember, the iwlist scan command worked fine with it too.
Now I upgraded to Edgy. The card is recognized and work (relatively) OK if you know the essid and IP, but it doesn't scan (I get a "interface doesn't support scanning"). 
I this forum ([http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=2619&](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=2619&)) is is stated that using the RutilT will allow to detect the neighborhoods networks, but when I try to do it I get and error. So, it only detect the networks if I enter the essid and other data. No support either for dhcp.
](*,) 
Trying to use the RaConfig2400 says that cannot locate the driver, but it is there!
Which bother me is why this worked fine in Dapper but not in Edgy, with the very same card/driver.

Any help will be very welcomed!

Cheers!

Mario

---

### Post by macozz on 2007-01-20
Bump!
Nobody out there has an idea?

---

### Post by macozz on 2007-01-22
Well, I get a partial solution in this thread:
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=18500#18500](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=18500#18500)

Is seems that RutilT has some issue in Edgy than can be "workarounded" launching RutilT as root. It worked for me, but may be better wait for a fix, as promised by Spy84464.

Cheers

---

