---
title: "Dell Wireless 1505 Draft AGBN mini-card + monitor mode?"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by PinkFloyd102489 on 2008-07-13
Ive been searching all over the forums and Google, but I cant figure out how to get the card into monitor mode. I found something about patching drivers, but that was for Ralink.

Anyone know how?

---

### Post by pytheas22 on 2008-07-13
You need to know what kind of chipset your wireless card has--the name that it's sold under doesn't mean much, because Dell doesn't actually make the guts of the card; it just sells them packaged together with other stuff.

Your card is probably Intel, or possibly Broadcom, but we need to know for sure.  Please post the output of:
```

lspci
lshw -C Network
```

and then we can figure out how to get support for promiscuous mode.

---

### Post by PinkFloyd102489 on 2008-07-13
It's the bcm4328 rev 03 chipset, using ndiswrapper.

---

### Post by pytheas22 on 2008-07-13
I don't think it's possible to use ndiswrapper for sniffing.  Its website says:
> 
Is master mode or promiscuous mode supported?

No! NDIS doesn&#8217;t support Master/Repeater/Monitor modes. The only modes supported are Ad-Hoc and Managed. Note that some drivers may support features that are not in NDIS e.g., showing signal noise and possibly Master mode, but they are proprietary and no documentation available for them, so such features won&#8217;t be supported by ndiswrapper.

In case that information is out-of-date, you can try:
```

sudo iwconfig wlan0 mode monitor
```

and see if it helps, but I doubt it.  You'll probably get an error message.

Did you try using the native Broadcom driver (b43 or bcm43xx)?  I'm not sure if it supports your chipset model but it may, but I am certain that it supports monitor mode.  Even if the driver doesn't work well enough to connect you to the Internet, it might still let you sniff.

Also, what exactly are you trying to do with monitor mode...aircrack, Wireshark?  Maybe there's a better way to do what you need.

---

### Post by PinkFloyd102489 on 2008-07-14
Id to like use aircrack, mainly because I have a small computer repair business and I like to do a "wireless audit" on their router. I know that NetStumbler for Windows wont use the card. bcm43xx-fwcutter works, so I'll try to switch to it.

---

### Post by pytheas22 on 2008-07-14
Yeah, you'll be better off with bcm43xx...and b43 would probably be even better than that if you can get it to work.  The last time I tried aircrack with a Broadcom card, it didn't work well at all (crashed a few seconds into monitor mode and couldn't inject), but that was more than a year ago and I think the Broadcom drivers have come a long way since then.

If your card doesn't work well and you're serious about aircrack, however, you may want to think about getting a cheap card that does sniff and inject well.  There are some cards with Ralink chipsets that work great and cost less than twenty dollars.  Most Atheros chips are also good, but will cost you more, and you'd have to buy a PCI or PCMCIA card (don't buy an Atheros USB card because it won't work well at all with Linux!).

---

### Post by PinkFloyd102489 on 2008-07-14
I have a PCMCIA slot, so I'd like to get one of those. What's a good Ralink chipset that you'd recommend? Ive been looking at BackTrack's compatibility list and a few Linksys Ralink PCMCIA cards are on there. Any specific one?

---

### Post by pytheas22 on 2008-07-14
I own a [DWL-G122 rev C]("http://www.amazon.com/s/ref=nb_ss_gw/104-9142255-1111149?url=search-alias%3Daps&field-keywords=dwl+g122&x=0&y=0") (I believe rev B also has an Ralink chip; don't know about other models) and [OvisLink Evolution W54USB]("http://www.amazon.fr/s/ref=nb_ss_w/403-6212074-2064465?__mk_fr_FR=%C5M%C5Z%D5%D1&url=search-alias%3Daps&field-keywords=ovislink+w54usb&x=0&y=0").   The first one has an rt73 chipset and the second one uses rt2570.  They're both USB dongles.  I don't know of any pcmcia cards that work well and I don't know if any pcmcia cards have Ralink chipsets.  I'm pretty sure there are some with Atheros chips, though, that would work well.  But then again, in a lot of ways, it's better to have a USB card--you can use it in desktops as well as laptops if you ever want to.

If you buy one of these, be careful to get the right revision number.  The chipset can change completely between revisions.  Most vendors aren't clear about which revision they're offering (amazon.com certainly isn't), so you may need to contact them and ask, or buy from a store where you can return it easily if it's the wrong revision.

Also, I think the OvisLink may be available only in France or Europe, but I'm not sure.  All of the references to it on the Internet seem to be in French, and that's where I bought it.  Also, I was never able to get my OvisLink to work for a normal Internet connection in Linux, although it works great with aircrack.  The DWL-G122 works very well for everything.

---

### Post by PinkFloyd102489 on 2008-07-14
Alright, well I'll keep that in mind. I know that Linksys USB dongles are like $30 at Walmart now, so I'll probably pick up one of those in the end.


Thanks a lot.

---

### Post by pytheas22 on 2008-07-14
No problem for the help, but if you do pick up a Linksys dongle, do your research first to make sure it's got a chipset that will work well with aircrack.  It probably won't say on the box, so you'll need to look it up online.  There are a couple dozen different kinds of chipsets out there, and their support on Linux (and therefore aircrack) varies widely, usually depending on how popular they are and how well their manufacturers cooperate with the open-source community.

Also, you may want to try with your Broadcom chip again.  I was reading on the aircrack pages that support for [Broadcom seems to be much better now]("http://aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=a2d9e1d2cc5966efce4742fcfbeca35f#broadcom_chipset_comments") than it was when I tried it a while ago.  Keeping in mind that results with your particular model of Broadcom chip may not necessarily be as favorable as those with Broadcom cards in general, check out [this page]("http://www.aircrack-ng.org/doku.php?id=broadcom") (bcm43xx) and [this page]("http://www.aircrack-ng.org/doku.php?id=b43") (b43) for instructions on patching the Broadcom drivers to support injection.  You will need to recompile kernel modules, which is a bit tricky (and I wouldn't try it on a system that you're not afraid to break beyond repair if something goes wrong), but there are instructions.

That said, maybe it is just easier to go buy a cheap card with a good chipset.

---

### Post by PinkFloyd102489 on 2008-07-15
Im on a Vista/Ubuntu dual boot, so if I screw up Ubuntu, I can just boot into Vista and wipe Ubuntu's partition to start over.

---

