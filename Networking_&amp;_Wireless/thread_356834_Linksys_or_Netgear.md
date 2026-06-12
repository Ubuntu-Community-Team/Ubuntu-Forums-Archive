---
title: "Linksys or Netgear"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2007-02-08
I am looking for a wireless PCMCIA card and the only place is radio shack. The only ones they carry are Linksys and Netgear. Do either of these have native Linux drivers?

If not, I was wondering if anyone had any experience with either of these brands and would have a model suggestion.

Thanks.

---

### Post by phossal on 2007-02-08
Is it possible for you to order one from the US?

---

### Post by ichan on 2007-02-08
I have taken my netgear adsl2 modem router back to be replaced for the second time in less than 12 months and the supplier had given me a new one without any question.  From what I hear, I am definitely buying a linksys next time I can afford one and just leave my netgear as a backup.

---

### Post by phossal on 2007-02-08
I have all Netgear products both at home and at work. They've worked flawlessly for me. Although I've owned Linksys products too, I have always preferred Netgear, if for no other reason than that Netgear products *look* so much better.

---

### Post by punx45 on 2007-02-09
unfortunately, manufacturers use different chipsets with different models, (or sometimes even different revisions of the same model) and it is these chipsets that really determine availability of drivers.   my only suggestion is to get model numbers and serial numbers off the boxes/from the webpage (if possible) and then google them to see what info you can get about what chipsets the cards may use.   also sites like linuxquestions.org usually maintain lists of compatible hardware.

but given a choice, its Linksys powered by Cisco FTW!

---

### Post by chewearn on 2007-02-09
I  bypass missing Linux driver and/or installation problem by using standalone Access Point (AP).  Might not be a good choice for notebook (extra equipment to carry around), but works great if you just need to connect a stationary desktop PC.

I have a mix of few models, trying one after another to find the best combination:

Linksys WAP54G - solid performance, support client mode, but not able to get WPA2 to work with another AP

DLink DWL-2100AP - also good, but same as Linksys, WPA2 not working with another model

Netgear WG602 - when I bought this a while back, client mode was not supported, but Netgear has a recent firmware update which fix that.  Best of the lot, because it is able to connect in WPA2 to another same model AP (but not to another Netgear wireless router, nor the Linksys and DLink).

Another point to note is, these are 802.11g AP; newer "n" or" pre-n" mode not supported.  But 802.11g speed is fine, if you mostly connect to the Internet, even at broadband speed.

---

### Post by banditti on 2007-02-09
This is on the router side, but check out [http://www.dd-wrt.com](http://www.dd-wrt.com) 

They have one Linksys and others replaced the os with LINUX!  Makes them a ton more reliable.

---

### Post by haz2a on 2007-02-09
Check the listings at: [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/).

Other useful info at:-
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[www.linux-wlan.org/docs/wlan_adapters.html.gz](www.linux-wlan.org/docs/wlan_adapters.html.gz)

Haz

---

