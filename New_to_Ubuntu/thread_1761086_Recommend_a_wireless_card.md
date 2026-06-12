---
title: "Recommend a wireless card"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-05-17
Can someone please recommend a brand for wireless card that is reliable with linux, ive always been wired but need wireless on my desktop pc for networking with people upstairs, seen as i always see people with wireless problems on here i thoguht id enquire before i spend the money. Preferably something that is easily available in the UK from novatech or somewhere similar.

---

### Post by TeoBigusGeekus on 2011-05-17
Advice: stay away from Broadcom.

---

### Post by Miljet on 2011-05-17
Anything that doesn't use Broadcom chioset.

---

### Post by NormanFLinux on 2011-05-17
I recommend an Atheros card. I think Belkin is a good bet since their wireless chipset is Atheros-based and is Linux-friendly.

---

### Post by CaptainMark on 2011-05-18
i cant seem to find many cards by belkin. Im referring to pci cards for desktops, not laptop cards (i find lots of them) both D-link and novatechs own brand seem to have lots of choices,

---

### Post by walt.smith1960 on 2011-05-18
This is not real up-to-date but it may be useful for you:
[http://linuxwireless.org/](http://linuxwireless.org/)

I agree with the Atheros chipsets, they seem to be pretty reliable.  Intel seems pretty good as well.  Realtek can be checkered.  You can't really rely on brand--for example Belkin may use a Realtek chipset in one adapter, Broadcom in another, Atheros in a third.   I  use USB wifi adapters so can't make PCI recommendations.  One thing to be aware of with PCI WiFi adapter though--make sure the antennas can be oriented such that the PC case isn't between the wireless source and the PCI card's antennas.  A big metal mass sitting between the antennas may not be conducive to reliable speedy connections.

---

### Post by CaptainMark on 2011-05-24
can anyone confirm how [this card]("http://www.novatech.co.uk/novatech/prods/networking/wirelessnetworking/wirelesspcicards/dlink/dwa-547.html") works out of the box. it uses an atheros ar5416 chipset but id like to know if it likely to work from the box on open source drivers before i buy it, it needs to work with live cds aswell as full install you see hence the need for out of the box conpatibilty

Thanks 
mark

---

### Post by 5149.5 on 2011-05-24
> **CaptainMark said:**
> can anyone confirm how [this card]("http://www.novatech.co.uk/novatech/prods/networking/wirelessnetworking/wirelesspcicards/dlink/dwa-547.html") works out of the box. it uses an atheros ar5416 chipset but id like to know if it likely to work from the box on open source drivers before i buy it, it needs to work with live cds aswell as full install you see hence the need for out of the box conpatibilty

Thanks 
mark

I just did a quick google and I saw some negative reports. I also saw some reports of using the ath9k driver. My netbook uses the ath9k driver and it required a one line conf file for full speed operation so I wouldn't call that out of the box capable and it would be a real problem for LiveCD.

---

### Post by beew on 2011-05-24
This one works out of the box and cheap too (bought it for $15). Tested on 10.04, 10.10 and 11.04.  Don't need to install any driver, plug in and connect.

[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

**EDITED:** Opps, sorry, I thought for some reasons that you are looking for a usb wireless card.

---

### Post by CaptainMark on 2011-05-24
It seems like there's a real leap of faith when it comes to buying a need wireless device on linux, if you already got a card that you want to see if it works just pop in a live cd but if you have Linux and want a new card its a gamble, I remember not too long ago it was the same with gpus, they've improved a lot so maybe WiFi cards will follow suit soon

---

### Post by beew on 2011-05-24
Here is something specific.  Atheros AR507EG works beautifully on my laptop ( ath5k for driver) Tested with Ubuntu 10.10 and 11.04 and Fedora 15.  This card seems to be working much better with Linux than with Windows as I was having a hard time connecting on XP (signal strength was always weak)

---

### Post by gandaran on 2011-05-25
> **beew said:**
> Here is something specific.  Atheros AR507EG works beautifully on my laptop ( ath5k for driver) Tested with Ubuntu 10.10 and 11.04 and Fedora 15.  This card seems to be working much better with Linux than with Windows as I was having a hard time connecting on XP (signal strength was always weak)
yes, the AR5007EG card works very well.
but why does Ubuntu (lspci) identify the card as AR5001 on my netbook while windows xp says its AR5007EG?

---

### Post by aeiah on 2011-05-25
how about the trusty Alfa AWUS036H? its what all the script kiddies use with aircrack to mess with wireless packets, hack WEP etc. its got great range, works out of the box, and is decently priced.

it isnt 'n', though

---

### Post by fractalman on 2011-05-25
I use a LM technologies LM-001 wifi usb adapter, it uses the zydas zd1211rw driver, it worked straight away on 11:04 out the box but on other installs i have had to patch the drivers (Backtrack 5 :D),  which is simple enough, there's plenty of documentation online,  I've been thinking about getting a proper wireless card and from what i've read online, the Atheros chipset seems to be a pretty safe bet.

---

