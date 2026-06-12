---
title: "Another USB wireless problem"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by etherizim on 2005-08-10
I, along with others that i have noticed seem to have problems with Ubuntu recognising USB wireless antenna's.

now i understand that not all wireless USB connectors are the same, but shouldnt they all have the same basic principles in there Drivers?

and would ubuntu recognise the drivers i have for it, if i reinstalled them on the Ubuntu partition EVEN if they are technically x86 format?

stupid USB wireless not being good, but it being wayyyy cheaper than a PCI wireless card >.<

---

### Post by etherizim on 2005-08-11
well after doing some searching, there are like 2 types of USB wireless that will work on linux.  one being anything based on the ATMEL chipset.  

and the other....something else.
here is a list of ATMEL chipset USB wirless pulgs: [http://atmelwlandriver.sourceforge.net/usbtable.html](http://atmelwlandriver.sourceforge.net/usbtable.html) 

you need there linux driver to get it to work, but sadly the NDiswrapper doesnt support USB wireless at this time.  sadly for me, im using a Dell 1180 USB wireless which is NOT based on the ATMEL chipset.

i believe somone should post a sticky or something giving full instructions and info on which wireless are supported and which arent.

this would have my job alot easier.  oh well.  im going ahead with the install but shall use windows as my default.

---

### Post by CamB on 2005-08-11
[QUOTE=etherizim]well after doing some searching, there are like 2 types of USB wireless that will work on linux.  one being anything based on the ATMEL chipset.  

and the other....something else.
here is a list of ATMEL chipset USB wirless pulgs: [http://atmelwlandriver.sourceforge.net/usbtable.html](http://atmelwlandriver.sourceforge.net/usbtable.html) 

you need there linux driver to get it to work, but sadly the NDiswrapper doesnt support USB wireless at this time.  sadly for me, im using a Dell 1180 USB wireless which is NOT based on the ATMEL chipset.

i believe somone should post a sticky or something giving full instructions and info on which wireless are supported and which arent.

this would have my job alot easier.  oh well.  im going ahead with the install but shall use windows as my default.[/QUOTE]
 *sadly the NDiswrapper doesnt support USB wireless at this time.*

Are you sure? I'm a total n00b and I got it to work (until I upgraded the kernel and found that ndiswrapper doesn't currently work with USB adaptors and 1gb of RAM).

---

### Post by etherizim on 2005-08-12
it will only work on the ATMEL chipset for USB wireless connectors.  that or no one seems to update anything....ever.

what USB wireless connector do u use?

---

### Post by akseli on 2005-08-13
[QUOTE=etherizim]well after doing some searching, there are like 2 types of USB wireless that will work on linux.  one being anything based on the ATMEL chipset.  

and the other....something else.
here is a list of ATMEL chipset USB wirless pulgs: [http://atmelwlandriver.sourceforge.net/usbtable.html](http://atmelwlandriver.sourceforge.net/usbtable.html) 

you need there linux driver to get it to work, but sadly the NDiswrapper doesnt support USB wireless at this time.  sadly for me, im using a Dell 1180 USB wireless which is NOT based on the ATMEL chipset.

i believe somone should post a sticky or something giving full instructions and info on which wireless are supported and which arent.

this would have my job alot easier.  oh well.  im going ahead with the install but shall use windows as my default.[/QUOTE]

Don't fret! The solution is near! Hehe, no, I'm not positive but you might want to try:

WLAN-NG
[https://wiki.ubuntu.com//HowToInstallTheWlanNgDriverInHoary](https://wiki.ubuntu.com//HowToInstallTheWlanNgDriverInHoary)

I used this tutorian in combination with the readme file that comes with the Wlan package and managed to install and get my USB adapter recognized.
Good luck!

---

### Post by CamB on 2005-08-14
[QUOTE=etherizim]it will only work on the ATMEL chipset for USB wireless connectors.  that or no one seems to update anything....ever.

what USB wireless connector do u use?[/QUOTE]
 I've got this rebadged, generic one:

[http://www.dse.co.nz/cgi-bin/dse.storefront/42fff16e020fc800273fc0a87f9906ce/Product/View/XH8227](http://www.dse.co.nz/cgi-bin/dse.storefront/42fff16e020fc800273fc0a87f9906ce/Product/View/XH8227)

(I suspect that link won't work for long).

It has a Prism chip of some sort.

Have a look on this list of stuff that works with ndiswrapper, if you haven't already.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

