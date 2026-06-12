---
title: "Wii -&gt; Ubuntu Laptop WAP (broadcom) -&gt; Ethernet -&gt; Web help"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Sarisar on 2007-06-25
So yes I should probably get a wireless router...

BUT does anyone know how to set up this Ubuntu laptop (Feisty) to have a WAP that the Wii can connect to.  I have a broadcom card that should be up and running properly... ish - have no wireless network to try it on though so it might not be.  It may be relevant (or maybe not) but I've updgraded from Dapper upwards on this machine and used the wrappers to get the card working.  I can see some wireless networks but they are all encrypted so don't know if it would actually work.

Yeah I know I'm awkward!

Cheers

---

### Post by spd106 on 2007-06-26
The Wii has no support for ad hoc, so you will have to use AP or master mode. Unfortunately this is not supported by ndiswrapper, nor by the bcm43xx-softmac driver include in Feisty. You will either have to compile the latest code from wireless-dev with mac80211 support or wait for Ubuntu 7.10 to be released in October.

Alternatively, I believe Fedora 7 has bcm43xx-mac80211 already built in, so you could try that instead.

---

### Post by Sarisar on 2007-06-26
Yeah I was afraid it would be something like that.  I wonder if I could get it working on a fedora live cd...

Anyway thanks for the reply :)

---

