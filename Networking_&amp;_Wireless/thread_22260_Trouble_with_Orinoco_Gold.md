---
title: "Trouble with Orinoco Gold"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by MalteL on 2005-03-26
I recently brought an Orinoco Classic Gold PC Card. It uses, as far as I remember, the Atheros chipset, and thus, I apt-got the package with the madwifi drivers in (kernel-restricted-something). But lspci doesn't say anything about it, and when I insert the card, dmesg cries out:

```
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
```

(Yes, 6 times). The driver seems to load without problems - when I do:

```
sudo modprobe ath_hal
sudo modprobe ath_pci 
```

dmesg answers:

```
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
```

And when I do

```
lsmod | grep ath
```

It outputs:

```
ath_pci                62504  0
ath_rate_onoe          10512  1 ath_pci
wlan                  116692  2 ath_pci,ath_rate_onoe
ath_hal               155504  1 ath_pci

```

What should I do?
Thanks in advance,
Malte

---

### Post by sMell on 2005-03-28
[QUOTE=MalteL]I recently brought an Orinoco Classic Gold PC Card. It uses, as far as I remember, the Atheros chipset[/quote]

It uses the orinoco chipset and the card was formerly known as wavelan

```
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
cs: unable to map card memory!
```

This is the pcmcia driver complaining.  The pcmcia bridge may not be supported.  The PCMCIA docs have more information on troubleshooting... Good luck

---

### Post by az on 2005-03-28
Are you using Warty or Hoary?

Is this bug relevant?  Please add info if it is:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6566](https://bugzilla.ubuntu.com/show_bug.cgi?id=6566)

---

### Post by MalteL on 2005-03-29
Thank you for your quick answers.

Azz: I am using Hoary.
The bug you send me (well, you know what I mean) doesn't really, after a quick glance, I will look closer at it soon, seems similar to my bug. 

sMell: > The pcmcia bridge may not be supported. Seems scary. Does it mean, that I can't use the card? The pcmcia-docs in /usr/share/doc/pcmcia didn't help me - but I will look in [http://pcmcia-cs.sourceforge.net/ftp/doc/](http://pcmcia-cs.sourceforge.net/ftp/doc/).

Thank you,
Malte

---

### Post by az on 2005-03-29
Try using warty.

You can try the Warty  live cd, if you do not want to start over.  Your card should work.

---

### Post by sMell on 2005-03-30
[QUOTE=MalteL]
sMell: . Seems scary. Does it mean, that I can't use the card? The pcmcia-docs in /usr/share/doc/pcmcia didn't help me - but I will look in [http://pcmcia-cs.sourceforge.net/ftp/doc/](http://pcmcia-cs.sourceforge.net/ftp/doc/).
[/QUOTE]

Try this page:
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html#ss2.5](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html#ss2.5)

---

