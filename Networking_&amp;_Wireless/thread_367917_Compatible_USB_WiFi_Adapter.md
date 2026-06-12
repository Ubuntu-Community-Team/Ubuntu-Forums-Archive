---
title: "Compatible USB WiFi Adapter?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by TomJr on 2007-02-22
Hello,

Well after spending the better part of one full day attempting to get my Via Unichrome video card running and finally succeeding, then spending the better part of the next day attempting to get my Broadcom 4318 up and running and failing miserably, I have resigned to simply go out and buy a USB WiFi adapter.  I post because I was hoping someone might point in the right direction as to an adapter than will just *work* without *any* screwing around *whatsoever*, as I just want something to get me wirelessly connected to the internet already.  Is there a list somewhere of USB adapters that will work without tossing runes, reading tarot cards, sacrificing a one horned goat, or recompiling the kernel?  I am running xubuntu 6.10.  Thanks for your time in advance...

Tom

---

### Post by OffAxis on 2007-02-22
try this site[http://ralink.rapla.net]("http://ralink.rapla.net")
support for the ralink chipset is built into Edgy 6.10
Is it perfect? No, but it's a good start (and you won't have to download a driver, just mess with the interfaces file and maybe the iptable)
hth

---

### Post by TomJr on 2007-02-23
Thank you I will be sure to look into getting an adapter from this list.

Tom

---

### Post by DapperMe17 on 2007-02-23
Tom Jr...


Hands down, go with the Linksys WUSB54G...Version #4. You can find them on eBay.


It will work out-of-the-box with Edgy, using a built-in driver.


Should you require encryption, either WEP or WPA, you'll simply need to configure the USB adapter within Edgy. (Seems like a daunting task...I've been through it! It's really very easy.
Search for my posts for the WUSB54G, as well as Wieman's.


If you chose this model, I'd be happy to help you through the process.

---

### Post by cliff01 on 2007-02-23
Is Version 4 the difference? I have a Vs. 1 type that won't work. Let me know before I spend the $$
Thanks!

---

### Post by blisteringblue on 2007-03-01
Complete Ubuntu novice here, just wanted to see what I could do with an old PIII laptop.

I now have it working perfectly with Xubuntu 6.10 and I have a wireless internet connection with a Netgear MA111 v1 USB adapter (had it in a drawer for years).

Although I made it hard for myself, in the end all it needed to work was linux-wlan-ng loading in xubuntu and then just use the built in system network settings panel to configure.

---

