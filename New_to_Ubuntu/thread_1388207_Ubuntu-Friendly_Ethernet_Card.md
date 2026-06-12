---
title: "Ubuntu-Friendly Ethernet Card?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Nicky1204 on 2010-01-22
Alright, so I've installed Ubuntu 9.10 on my really old desktop. It's an HP Pavilion 4550Z if you need to know. Anyway, It's never been connected to the internet. I would like to connect it, but it doesnt have an ethernet port. I've been looking at ethernet cards, but, the driver CDs are only for Windows, so I'm afraid if I buy a card and install it, I may not be able to install the drivers and it wont work. So what I'm asking is, has anyone found an ethernet card with drivers that will work with Ubuntu?:confused:

---

### Post by steveneddy on 2010-01-22
Any modern Ethernet card should do the trick.

Even the house brands should have a supported chip.

cheers

---

### Post by Nicky1204 on 2010-01-22
> **steveneddy said:**
> Any modern Ethernet card should do the trick.

Even the house brands should have a supported chip.

cheers
Okay, cool. Thanks a lot! :D

---

### Post by pirateghost on 2010-01-22
drivers?  what are those?

:P

---

### Post by Nicky1204 on 2010-01-22
> **pirateghost said:**
> drivers?  what are those?

:P It's like uh, the software that makes certain hardware work correctly.

---

### Post by Nicky1204 on 2010-01-22
> **pirateghost said:**
> drivers?  what are those?

:P
Oh, wait...was that sarcastic? XD

---

### Post by HereInOz on 2010-01-22
Try to avoid cards with Broadcom chips.  If you go with a card using an Atheros chip, you will have absolutely no issues at all.

---

### Post by Flimm on 2010-01-22
> **Nicky1204 said:**
> Oh, wait...was that sarcastic? XD
Yes it was. ;) Linux tries to include drivers by default, so in an ideal world, you would never need to install drivers to get a device to work on Linux.

Realistically, some manufacturers do not submit drivers under an open source license compatible with the GPL to the Linux kernel. In these cases you either use what volunteers have reverse-engineered, or you install the closed-source driver.

I've only once come across an Ethernet card that didn't work in Ubuntu, and at the time, I found a working Linux driver online. A year later, I re-installed the latest version of Ubuntu (9.10) and the card worked by default. So there's really no need to worry about Ethernet card drivers on Linux. Even Wi-fi is getting pretty good on Linux.

---

### Post by lisati on 2010-01-22
[This]("http://www.dse.co.nz/dse.shop/4b5a595101e5063c2743c0a87f3b0635/Product/View/XH8265") one works with Ubuntu - I have one in my backup machine (which runs Ubuntu 6.06) and I had one in my main desktop for a while.

---

### Post by pirateghost on 2010-01-22
> **Flimm said:**
> Yes it was. ;) Linux tries to include drivers by default, so in an ideal world, you would never need to install drivers to get a device to work on Linux.

Realistically, some manufacturers do not submit drivers under an open source license compatible with the GPL to the Linux kernel. In these cases you either use what volunteers have reverse-engineered, or you install the closed-source driver.

I've only once come across an Ethernet card that didn't work in Ubuntu, and at the time, I found a working Linux driver online. A year later, I re-installed the latest version of Ubuntu (9.10) and the card worked by default. So there's really no need to worry about Ethernet card drivers on Linux. Even Wi-fi is getting pretty good on Linux.
except for those friggin broadcom wireless on dell laptops......those things are a nuisance...i mean i have to actually hook it up to an ethernet cable to download the drivers for it....LOL


there are only 2 times i have ever needed drivers for linux (dell broadcom wireless, and raid card drivers [highpoint rocketraid 2640])

---

