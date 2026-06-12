---
title: "Going Wireless on a Desktop"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by DeanoCYM on 2009-09-17
Hi there,
I've recently moved into a rented house. Not having telephone cables upstairs or being able to drill holes all over the place means that I'm going to have to go wireless on my desktop.

I'd prefer to install a PCI card rather than a USB adapter. I'm using _[this]("http://h18000.www1.hp.com/products/quickspecs/11632_div/11632_div.HTML#Standard%20Features")_ old machine with a jaunty install (the small form factor model). One PCI slot is being used a graphics card, but there is still one free.

Any ideas what card I should buy?

Thanks for your help,
Rhys.

---

### Post by bumanie on 2009-09-17
I believe edimax products use chipsets that have drivers in the linux kernel - start your research at[ edimax]("http://www.edimax.com/en/produce_list.php?pl1_id=1&pl2_id=")

---

### Post by mapes12 on 2009-09-17
Hi

I have bought both a PCI and PCMCIA wifi cards from these people. They are great. Just install and it works:

[http://www.linuxemporium.co.uk/products/variations/wireless-1.html](http://www.linuxemporium.co.uk/products/variations/wireless-1.html)

UK based.

---

### Post by 3rdalbum on 2009-09-17
Why don't you have a look at Homeplug networking; it's Ethernet over your home's electrical wiring. I used to use wireless to connect my desktop to my network, but it was unreliable, and got worse when they changed the wireless stack in the kernel. The Homeplug is much more reliable and more secure (the signal stops at the meter box).

It's literally just a box that plugs into a power point, and connects to your computer via Ethernet port. No special drivers needed, it's completely network transparent. This means that your network doesn't actually "see" the Homeplug devices; they just perform the same function as an Ethernet cable.

As I mentioned, I have two Netcomm Homeplug AV 200mbps boxes (you get a "starter kit" with two boxes). I'm just about to add to it with an additional TP-link-branded Homeplug AV box.  The TP-Link ones are a bit cheaper and probably just as good - they use the exact same standard.  Take a look on eBay, I'm sure someone near you will be selling a TP-link Homeplug starter pack.

---

### Post by DeanoCYM on 2009-09-17
Ok thanks for the quick replies, i will look into all of them now. 3rdalbum that sounds very interesting indeed.

---

