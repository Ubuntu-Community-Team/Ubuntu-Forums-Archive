---
title: "Philips SNU6500 WiFi card..."
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by thomas ll on 2006-11-14
Hey!

I am realy new i Ubuntu (6,10). But i cant got on the network.
I have a Philips SNU6500 card.
Can some one help me?

Since i dont know any thing about Ubuntu i dont know what kinf of information you need. so just ask..

---

### Post by Harry_Sack on 2006-11-17
I'm working on the same problem right now.
You should use ndiswrapper I think.
Get drivers either from the cd that ships with the card, or from here: [http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?tmplt=Cps&scy=GB&slg=ENG&cat=WIRELESS_PC_NETWORKING_CA&sct=PC_AV_LINK_ADAPTERS_SU&grp=MONITORS_PC_PERIPHERALS_GR&session=20061117100004_89.10.16.181&ctn=SNU6500/00&mid=Link_Software&hlt=Link_Software]("http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?tmplt=Cps&scy=GB&slg=ENG&cat=WIRELESS_PC_NETWORKING_CA&sct=PC_AV_LINK_ADAPTERS_SU&grp=MONITORS_PC_PERIPHERALS_GR&session=20061117100004_89.10.16.181&ctn=SNU6500/00&mid=Link_Software&hlt=Link_Software")
Use ndiswrapper to load the .inf-files.

I'll post back if I make it work.

---

### Post by Harry_Sack on 2006-11-20
I haven't found any soulution yet, as I am trying to configure an acx111 instead. But I found something that might help.

From the [Norwegian ubuntu]("http://ubuntu.no/EdgyGuider#snu6500") site:

Type this in a terminal
```
$ wget http://bitstorm.no/ubuntu/snu6500/snu6500.sh 
$ sh snu6500.sh
```

try prefixing it with sudo if it gives permission errors etc.

good luck!

---

### Post by okuzcuk on 2007-09-23
now &#305;'m having this problem. using usb adapter SNU6500 and wanna use it in ubuntu. can't find a linux driver for it. anyone have the solution? thanks from now.


edit : at the top a friend gave a code from a site 

> 
$ wget [http://bitstorm.no/ubuntu/snu6500/snu6500.sh](http://bitstorm.no/ubuntu/snu6500/snu6500.sh) 
$ sh snu6500.sh


but it doesn't work. no such web site.


&#305; just send an e-mail to philips. ask about a linux driver. when they came back i will say to you. and &#305; found NdisWrapper. i will try it now. see what happens.

---

