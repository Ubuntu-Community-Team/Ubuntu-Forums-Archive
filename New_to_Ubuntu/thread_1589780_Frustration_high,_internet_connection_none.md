---
title: "Frustration: high, internet connection: none"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Spottydog on 2010-10-06
ok - I confess, I am a klutz at all this.  Have a Dell Inspiron 6000.  It has an internal network adapter (ethernet card?) - but I don't know what the make/model is - how do I look that up? 

It will not work.  I am running ubuntu 9.10 and I DID have wireless internet using a Belkin Wireless G USB adapter  However the belkin stick got broke :(   I purchased another one tonight - got a Belkin N150 on the assumption (mistaken) that I would be able to just plug it in and it would work! Of course, that didn't happen.  So, rather than spend hours trying to figure out how to get THAT to work, I've spent hours instead trying to figure out how to get the internal network card to work but I'm stumped - basically because I cn't even find out what type of network card is installed.  I did a sudo lshw and I believe the network card is  a broadcom ethernet interface BCM 4401 - BO.

If anyone has an easy way for me to get my wireless internet connection working, I'd be so grateful because I love using ubuntu, but I have to confess, most of the instructions and jargon is all gobbledygook to me!!

Thanks so much.

---

### Post by e79 on 2010-10-06
> **Spottydog said:**
> .... I've spent hours instead trying to figure out how to get the internal network card to work but I'm stumped - basically because I cn't even find out what type of network card is installed.  I did a sudo lshw and I believe the network card is  a broadcom ethernet interface BCM 4401 - BO.

Type:
```
lspci
```Here's an example of my own output (trimmed of course since lspci gives you much more info):

"**04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)**"

You will then be able to determine which Ethernet adapter you have.

Hope this helps

---

