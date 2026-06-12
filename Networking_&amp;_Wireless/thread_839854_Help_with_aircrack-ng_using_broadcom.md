---
title: "Help with aircrack-ng using broadcom"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by AnonPrime on 2008-06-24
Im trying to get my wireless card to work with aircrack-ng in ubuntu, is there anyway to get a Broadcom BCM4328 (rev 03) to work without using ndiswrapper?

---

### Post by pytheas22 on 2008-06-24
I think (but could be wrong as I don't own one myself) that that chipset unfortunately is still not supported by any native driver.  In any case I don't think Broadcom cards will be able to inject reliably (at least, I know they couldn't about fifteen months ago).

If you want to play with aircrack, I'd recommend buying a cheap (20-30 dollar) USB stick with an RaLink chipset.  If you need suggestions on which ones in particular, I can make them.

---

### Post by AnonPrime on 2008-06-25
hmm, any recommendations on which one i should get?

---

### Post by pytheas22 on 2008-06-25
I used a [DWL-G122]("http://www.amazon.com/D-Link-DWL-G122-Compact-Wireless-Adapter/dp/B0002DQUHC/ref=sr_1_1?ie=UTF8&s=electronics&qid=1214406326&sr=8-1") (it's a little more expensive now than it was last year), which has an rt73 chipset.  I also used an [Ovislink W54USB]("http://www.amazon.fr/Ovislink-EVO-W54USBV2-wireless-802-11g-Mbps/dp/B000MRP1G4/ref=sr_1_1?ie=UTF8&s=electronics&qid=1214406586&sr=8-1") (really good price, but looks like it may only be available in Europe, which is where I bought it originally), with an rt2570 chipset.  You can't inject using the default RaLink drivers that come with Ubuntu, but if you blacklist them and install the legacy drivers from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page"), these cards work really well, in my experience.

The DWL-G122 needs to be revision C1 and the W54USB is version 2.  This is important, because the other revisions use different chipsets, which means that they may as well be completely different devices as far as Linux is concerned.  Unfortunately most sites don't mention which revision the product is, since Windows users don't care.  If possible, you might want to see if you can buy one of these cards at a decent price in a store, where you could return it if it turns out not to be the right version, or try to contact the online sellers and see if they'll confirm which versions you'll get.

The aircrack people also have a list [here]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers#list_of_compatible_adapters") of adapters that they think work best.

---

