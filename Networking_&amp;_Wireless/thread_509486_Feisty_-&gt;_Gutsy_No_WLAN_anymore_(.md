---
title: "Feisty -&gt; Gutsy: No WLAN anymore :("
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by DaVinciXL on 2007-07-25
Hey everyone.

I just installed a fresh 7.10 Kubuntu on my Laptop and am now experiencing some trouble with my WLAN. I chose to use KUbuntu from 6.10 on because it was the only distribution to recognize, install and set up my WLAN chip right out of the box correctly.

With 7.04 I could even use it from the LiveCD.

Now after having installed 7.10 and all the driver packages and restricted materials: still no WLAN interface is set up.

How can that be done?
If I go to system settings and enter the network stuff I cannot see any button saying "add interface" or something similar.

At home I can plug in a cable but for work and university I need WLAN to work... and since this was no problem in 7.04 I'm sure I'm just missing something here.

Almost forgot: lspci describes my WLAN chip as
> 04:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Anybody experiencing similar problems?
Any solutions so far?

Regards,
Sebastian

---

### Post by tgoose on 2007-07-25
You do realise that Gutsy is for testing only at this stage, right? It's not for everyday use at all. I have the same problem with my Ralink chipset Belkin card.

---

### Post by Èync on 2007-07-25
you have to wait two months for offical release :/

---

### Post by DaVinciXL on 2007-07-26
Of course I know that Gutsy is for testing purposes at the time being.
But that's nor reason for my WLAN chip not to work especially when it did work quite fine with the last release. :)

No, realy, I'm pretty pleased with Tribe3. (K)Ubuntu is amazing - even without WLAN.

I just wanted to know wether this is a general problem or if I've overlooked something or am just plain stupid.

@tgoose: did you get your WLAN up and running manually by any chance?
I read some tutorials but those weren't of great help - probably because none of them was written for Gutsy but for Feisty...

---

### Post by kevdog on 2007-07-26
Compile the serial monkey rt61 drivers from source and reinstall them.  That should work.  Here is a general guide for the rt73 chipset, read it over but substitute 2500 everywhere rt73 is listed and dont blacklist the rt61 drivers:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by DaVinciXL on 2007-07-26
Thanks.

But I already knew that guide... somehow that doesn't work for me. Neither with the sources that come with Ubuntu, nor with the freshly downloaded ones...

Guess I'll really have to wait...

---

