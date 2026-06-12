---
title: "Motorola Wireless Adapter Not Working"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by dniezby on 2009-03-09
Model Number: WN825G

Anyone know how I can get my wireless notebook card working?

I place the card into my PCMIA card slot but it doesn't turn on.

It works in Windows but I cannot figure out how to get it to work for the life of me.

Please help, cause I can't update anything at all.

---

### Post by dniezby on 2009-03-09
Just an update:

I went through the Administration / Hardware Test and it does find the card:

Broadcom Corporation BCM4401 100Base-T(rev 01)
Broadcom Corporation BCM4306 802.11b/g Wireless
LAN Controller (rev 03)

I click yes and it won't connect to the internet.

---

### Post by avtolle on 2009-03-09
I don't have a Broadcom card, but you will need to get the linux driver for it installed. Look under System>Administration>Hardware Drivers and see if there are drivers there for your card. You will need to have a wired connection to the internet to download the driver, IIRC from other posts.

---

### Post by dniezby on 2009-03-11
> **avtolle said:**
> I don't have a Broadcom card, but you will need to get the linux driver for it installed. Look under System>Administration>Hardware Drivers and see if there are drivers there for your card. You will need to have a wired connection to the internet to download the driver, IIRC from other posts.

There are no drivers listed - at all - when we click on Hardware Drivers, and for some reason, my onboard Ethernet card doesn't work...But it stopped working in XP as well. (Think that one is a hardware problem.

Is there a way that I could download stuff to a thumbdrive and install it?

One odd thing is that entering in:```
ndiswrapper 
``` is lists my buddy's ethernet card and broadcom card but it says that the wireless card is Disabled.

BTW, This is my buddy's computer not mine. I don't even have ndiswrapper installed on my Ubuntu and everything works fine.  This is why his system is driving me insane.  Confused as to how my installation and my setup was so trouble free it baffles me as to why I'm having such problems getting his Ubuntu set up.

---

