---
title: "Looking for a compatible gigabit network card"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by eagle101 on 2006-08-29
Hi all,

I'm looking for a PCI gigabit network card to replace my 3C509-TX.  

I looked on the Ubuntu HCL, and it does list the Etherlink III NIC and compatibility with systems like dell etc, but it doesn't give any PCI card info (from what I've seen).

Could someone post what Gb PCI card they use and their success with it?  Or point me to a thread where this has already been discussed?

Thank you,
David

---

### Post by ciscosurfer on 2006-08-30
I would maybe choose a card that's completely compatible (no hiccups, and according to the list)

---

### Post by eagle101 on 2006-09-01
Hi, from my previous post:

>I looked on the Ubuntu HCL, and it does list the Etherlink III NIC 
>and compatibility with systems like dell etc, but it doesn't give 
>any PCI card info (from what I've seen).

The only card it mentions is the EtherLink III:
In Terminal type: /sbin/modprobe 3c509

I think this was a ISA with a PCI upgrade (10Mb)

Am I looking in the wrong place in the HCL?  There doesn't seem to be much there for networking.  I am looking at:

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

I've looked for "gigabit network" and gigabit hardware on the forums but haven't found any hardware threads.

I was just looking for a few people that had Ubuntu and 1000Mb & wanted to say "hey this is what I have" & opinions.
Thanks,
Dave

---

### Post by ciscosurfer on 2006-09-01
Unfortunately, the UDSF doesn't have much of an HCL...try these from Ubuntu:

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

and this one as well:

[http://www.ubuntux.org/linux-hardware-compatibility-list](http://www.ubuntux.org/linux-hardware-compatibility-list)

---

### Post by eagle101 on 2006-09-01
Thanks!  Just what I was looking for.  I didn't know the wiki had hardware info.

-Dave

---

### Post by cylon359 on 2006-09-03
I've used add-in e1000 (Intel) PCI cards, and they work quite well.  They may cost a bit more than some of the other cards (which I haven't used).

---

