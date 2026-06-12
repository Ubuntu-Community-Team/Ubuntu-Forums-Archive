---
title: "OK, so what wireless chipsets DOES Ubuntu support?"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by justinj100 on 2006-08-01
I am a recent Linux (Ubuntu) convert and have in a relativley short period of time, installed 6.06 on to a number of machines. 

with all desktop machines, networking (wired) has been detected and works as it should. No problem. However, with every laptop I have installed it on, the wireless network does not work. the latests, an Acer has a chipset that is not supported. there is a messy work around but it is still not garanteed to work and I certainly have not got it going yet.

MY question is this. Is there a suported chipset list some where which will enable would be users the ability to see if what thye have will work ahead of an install? this would help any propsectful, would be user having to surf Ebay trying to find a card that DOES work with their Linux install after the event!

Thanks in advance!

JJ

---

### Post by Ares Drake on 2006-08-01
In case you find a list please let us now. If such a list does not yet excist, lets start it.

I am running a IPW2100 (first generation Centrino) and it works out of the box in Breezy 5.10 and Dapper 6.06.

---

### Post by tturrisi on 2006-08-01
look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and here:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by Bezmotivnik on 2006-08-02
> **justinj100 said:**
> 

MY question is this. Is there a suported chipset list some where which will enable would be users the ability to see if what thye have will work ahead of an install? 
No, not realistically.

"Supported" in Linux doesn't mean "flawlessly supported in all installations with all native chip features easily accessible."

RT2500-based wireless devices (extremely common in notebooks and   PCI cards) are *supposed* to work adequately if you do not need easy GUI access to such common features as WPA2.  

Unfortunately, sometimes they just don't work, even when recognized and loaded in Ubuntu.  Why?  Who knows?

Wireless is an area where Linux in general drastically needs more work.  Even nominally "supported" devices don't always work very well.

I've been following this issue closely for over a year now, and that's still the bottom line.

---

