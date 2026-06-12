---
title: "I can't see wireless netorks with one nic, but with my other nic i can."
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by tee2 on 2007-01-16
I can't use oneof my wnics, a Ubiquiti 300mW SRC. It can't even see any networks:
```
tee@tee-laptop:~$ iwlist ath0 scanning
ath0      No scan results

```

I know that  there are networks though because ewhen I do the same on my working wnic, i can see networks:

```
tee@tee-laptop:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0D:3A:21:CA:63
                    ESSID:"MSHOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    Extra: Last beacon: 468ms ago

```


What could be causing this?

---

### Post by handy on 2007-01-16
Sorry to say this, but I think that you should think yourself lucky that you have a wireless card that works with Linux!

Wireless seems to be the toughest area for Linux at the moment, due to closed source firmware/drivers & the popularity of wireless, which is creating huge amounts of stress for users & developers alike!  The develpers understand the problem, most of the users feel far less sympathetic... :-k

---

### Post by SuperAl on 2007-01-16
Handy!
My dear Linux guru,
Its only a matter of doing things the right way around - first, find out what works with Linux and second, buy it.
Doing it the otherway around means buying Windows.

Examples: Dlink520 bought on a whim. Nice try but no cigar - no Linux.
Asus PCI wifi card, lucky draw, bought on a whim, large cigar.
Belkin PCI 7000 wifi card,  researched on PCworld website, check on Linux forums, pop up to shops on a Sunday, bingo, another cigar.
IBM R50 laptop, built in wifi works out the box with Pebble Linux.

But for all this, Tee2 still has his problem...

kind regards

SuperAl

---

### Post by handy on 2007-01-16
First time I've ever been called a guru, don't know who gets the cigar for that one?! lol

I certainly agree with your strategy, unfortunately for many notebook user's they get what they get when it comes to wireless, & mostly they aren't as savy as you as far as researching what is or is not supported in the various Linux distro's.  Then there are those of course that didn't give Linux a thought when they purchased their notebook, or whatever type of computer.

I personaly consider wireless to still be very immature technology & I won't even contemplate using it.  I like cat-5 cable, & it's limitations don't impinge on my freedom one little bit right now.

---

### Post by tturrisi on 2007-01-16
atho = atheros chipset = madwifi driver which is available in the linux-restricted-modules, have you installed the restricted modules for your kernel?

---

### Post by tee2 on 2007-01-16
> **tturrisi said:**
> atho = atheros chipset = madwifi driver which is available in the linux-restricted-modules, have you installed the restricted modules for your kernel?

Yes.

---

### Post by tturrisi on 2007-01-17
What antenna are you using?  afaik, you have to use an external antenna or pigtail w/ that card.
That card has no internal antenna:
[http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail](http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail)

---

### Post by tee2 on 2007-01-17
> **tturrisi said:**
> What antenna are you using?  afaik, you have to use an external antenna or pigtail w/ that card.
That card has no internal antenna:
[http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail](http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail)

I'm using this antenna, [http://www.data-alliance.net/servlet/Detail?no=6](http://www.data-alliance.net/servlet/Detail?no=6)

---

### Post by tturrisi on 2007-01-17
Put the ath0 card in, reboot & post the contents of
sudo gedt  /var/log/dmesg

---

