---
title: "Edimax EW-7128g Chipsets"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by Killimor on 2007-07-02
I want to go wireless and need a pci that is most easily installed without too much technical knowledge. I am currently thinking that the Edimax EW-7182g is the most compatible with Ubuntu 6.06 which I have recently installed.  (I could be wrong with that assumption though!!  Advice would be welcome.).

But I am hopelessly confused and utterly out of my depth when it comes to chipsets despite intensive googling and reading.  

On one site ( [http://www.linuxemporium.co.uk/products/wireless/#pid88170](http://www.linuxemporium.co.uk/products/wireless/#pid88170)), it says that the device has the RT2561 chipset.   But on another site ([http://openforeveryone.co.uk/perifs3.php?id=11](http://openforeveryone.co.uk/perifs3.php?id=11))  it says the same device is based on the rt61 chip.   Both claim to be Linux compatiible   But  on most sites that offer the Edimax for sale, they don't state anything at all about what chipset is used.

So, does it really matter what chipset is used in the Edimax EW-7128g? Could I buy either kind and assume  it will install reasonably painlessly in Ubuntu Dapper 6.06. 

I don't want to make yet another expensive mistake (please don't ask for details) in trying to go wireless with Ubuntu Dapper.   

tia,
Killimor

---

### Post by odiseo77 on 2007-07-02
Hi, I have exactly the same card (Edimax EW-7128g) and it works 'out of the box' on Ubuntu (tried it on Dapper, Edgy and Feisty). If you're concerned about the driver, it uses the rt2500 open source driver from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"), but as long as its recognized 'out of the box' by ubuntu, who cares about the driver ;)

P.S.: There's only one issue with this card: when using the beta drivers from serialmonkey (which I think are the ones Ubuntu uses) on an hyperthreaded CPU (as I am) , your system might turn unstable sometimes suddenly; so, if you're using an hyperthreaded CPU you might want to install the [cvs driver]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz") (I've to do this btw, but I've been to lazy lately :p :D )

Greetings.

---

### Post by Cadmus on 2008-04-08
It seems this card is perfect for ubuntu from everything I've seen, and it only costs £10 at the moment, it's almost tempting to get a whole crate.

---

### Post by odiseo77 on 2008-04-08
Yes, it's a good card. Has native linux drivers which have been included in the 2.6.24 kernel, so in the future should be supported by any linux distro out of the box. However, there are some minor issues with wpa connections and hidden AP's not working fine with the new generation driver (the rt2x00 one), but it's something you can easily solve by installing the "legacy" driver. I guess with its recent inclusion in the 2.6.24 kernel there are big chances all these issues are quickly fixed with future kernel releases.

---

