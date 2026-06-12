---
title: "Share internet connection - desktop via bluetooth to iMac to internet"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Gus Skink on 2008-07-18
I have a desktop running Hardy with a bluetooth adaptor. 

The bluetooth connection to my iMac (10.5.4) works.

The iMac is on a cable modem to internet.

I want to share this connection via bluetooth with the Hardy desktop. 

I don't want to run a cable as they are at opposite ends of the house and I have no router. I have Hardy on the iMac, but just want a second internet machine.


Is this do-able at all or is it time for a wireless router and go that way?

---

### Post by mbsullivan on 2008-07-22
*Bump*

... this applies to me in no way, but it's an interesting question. My guess (and it is just that) is that there is no *easy* way to do it.

That being said, I do believe it may be possible. My guess is the way to go about this would be to:

(1) Emulate a TCP/IP connection over the bluetooth link
(2) Share this "Ethernet" connection 

I must admit that I have very little experience with Bluetooth at this point, so I took an aside to do some research on (1). You can probably skip the next few paragraphs if you'd like, but I'll stick them in, anyway.

There seems to have been a fair amount of interest in "IP over Bluetooth" around 2000, and some of the reasons for this interest is to do precisely what you want to do, see:

[http://www.ietf.org/proceedings/00jul/SLIDES/ipobt-agenda/sld010.htm](http://www.ietf.org/proceedings/00jul/SLIDES/ipobt-agenda/sld010.htm)
[http://www.iab.org/documents/workshops/IAB-wireless-workshop/talks/BT-overview.ppt](http://www.iab.org/documents/workshops/IAB-wireless-workshop/talks/BT-overview.ppt)

There are a smattering of other academic papers on the subject, but none seem to be particularly recent.

One "gotcha" about this whole thing is that the throughput of the Bluetooth connection is much less than one might expect from an Ethernet connection (wireless or otherwise). See Figure 2 of [this paper]("http://www.telecom.lth.se/panda/research/publications/kihl_networking2000.pdf")... The maximum throughput you can expect (with an idealized link) for TCP/IP over Bluetooth is less than 700 kbit/s (about 80 kB/s), and this decays with the presence of any dropped packets. So, in reality, the transfer rate will be much slower.

That study focused on Bluetooth 1.x, which has a max throughput of 1 Mbit/s. Being optimistic, a newer Bluetooth device might get up to three times that speed, which is still incredibly slow compared to other Ethernet links. So, even if you got it working it may not be "worth it" for you.

So... now we get to the "acutally doing it" part. This is a bit fuzzier, but it seems to be possible with the Ubuntu bluez stack by setting up a Bluetooth Personal Area Network (PAN). The network emulates an ethernet interface, so it can be shared.

See (in no particular order): 

[http://samiux.wordpress.com/2007/07/02/bluetooth-networking-with-windows-mobile-5-under-ubuntu-704/]("http://samiux.wordpress.com/2007/07/02/bluetooth-networking-with-windows-mobile-5-under-ubuntu-704/")
[http://www.howtoforge.com/bluetooth_pand_debian_etch]("http://www.howtoforge.com/bluetooth_pand_debian_etch")
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=598890]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=598890")
[http://www.everythingq.com/forum/bluetooth/bluetooth-pan-an-alternative-to-802-11b-g-10549.html]("http://www.everythingq.com/forum/bluetooth/bluetooth-pan-an-alternative-to-802-11b-g-10549.html")

*Note: You can consider your Mac the "phone".*

After you get the interface created at /etc/network/interfaces, you should (hopefully) be able to share the connection using Firestarter. For examples, see:

[http://ubuntuforums.org/showthread.php?t=103881]("http://ubuntuforums.org/showthread.php?t=103881")
[http://ubuntuforums.org/showthread.php?t=503287&highlight=share+internet+connection+documentation]("http://ubuntuforums.org/showthread.php?t=503287&highlight=share+internet+connection+documentation")

As for speed, people [here]("http://www.everythingq.com/forum/bluetooth/bluetooth-pan-an-alternative-to-802-11b-g-10549.html#post70827") got widely varying speeds up to 450 kbit/s. Might be fast enough, might not (depending on your needs).

Sorry if this is a bit hackish... Like I said, I don't have any Bluetooth devices or experience in this sort of thing. Anybody else have any input?

Lemme know what you think, and I'd be happy to (offer my meager) help if you want to try and set up a PAN and share the connection.

Mike

---

