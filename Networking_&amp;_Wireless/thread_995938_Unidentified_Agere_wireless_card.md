---
title: "Unidentified Agere wireless card"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by priegog on 2008-11-28
Hi. 
I'm sick of my wireless being restricted to 1MBps, so I'm looking into buying a minipci card off of ebay. What I want is a card that will work out of the box and be able to use all of it's features (like those special modes needed to run ethereal/wireshark, and which cannot be accesed in cards that use ndiswrapper or the b43 driver), as well as being able to connect at decent speeds. As far as I know all the atheros cards would be the way to go, but I've got my eye on a particular card only identified by the brand agere. My unfruitful googling has only yielded the fact that some of those cards use the orinoco chipset, which are very well supported too. I asked the seller to tell me all the info he could gather from the chip itself, and here is what he replied: ```
Hello

I dont have a caera that can take picture readable so here is the infos on the card 1136M058059 , 3143 , f03and on one chip agere wcnd 2001 , t-hs2t 015168 , n4080sv4kw , 0308k 3669225 and on the other chip agere wl600101ly , 0317s , 9697925

the mac adress is 0090965cdc00
Thanks for looking

```
So I don't know what to make of this. Googling took me to the french ubuntu forums to a post that said a guy with agere wl600101ly had to install ndiswrapper, but not much else. 
Got any ideas? 
And furthermore, is there a page where I can cross-reference model numbers for other cards and see if they work well with linux? What else should I know? What brands should I pursue and avoid? 
Thanks.

---

### Post by priegog on 2008-11-28
Ugh, the thing complicates further. I found another candidate, and Atheros ar5bmb5, and upon googling I found that it causes some problems and they need to be activated using the restricted hardware manager. I tought atheros was a safe bet? Or does the needing of the restricted hardware manager not necessary mean you can't get very low-level access to the card and that it won't work perfectly? I'd be fine having to use the restricted hardware manager if that was the case, but alas, I don't know what the case is.

---

### Post by gnusci on 2008-11-28
I will recomend you to give a look to the following page:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by priegog on 2008-11-28
Thanks.. I should have mentioned I already had gone tru all those articles (it's on the sticky of this forum) And none of these cards show neither in the supported or non-supported lists. Hence my question. But thanks anyways.

---

