---
title: "Can USB wireless cards work in ubuntu"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by manish_singh2 on 2014-09-17
I have broadcom wireless card in my laptop, which doesn't work in ubuntu, Kali etc. linux distros. I have tried a lot, but even when it works packages like aircrack-ng doesn't doesn't function properly.  I am now really sick of all this. At the end i am thinking of using a USB wireless adapter.  Can it work fine. If yes which one are good enough. or should i replace the card with Atheros or others

---

### Post by weatherman2 on 2014-09-17
Some USB cards work well in Ubuntu.  I have not used any with Ubuntu 14.04.  Sometimes drivers change with new kernel releases, so I hesitate to recommend USB cards I've used in older versions.  Maybe others can.

You may still be able to get the Broadcom card to work - have you posted a help thread here for it?

I have replaced many laptop wireless cards.  Sometimes it is easy and cheap to do.  But what kind of laptop is it?  Know that if you have a Lenovo/IBM or HP laptop, it will be difficult to replace the wireless card because those manufacturers "whitelist" their wireless cards.  If you try to install a different wireless card that isn't in the BIO's "whitelist" you will not even be able to POST or power up without removing it.

Other brands - Dell, Acer, Toshiba, etc. should be fine.

If your wireless card is older than about 2006, it may have the older style mini-PCI card (bigger).  2006 or newer has more options for mini-PCI wireless cards.  I like the Intel 5100 - automatically supported in Ubuntu, usually available on eBay used for about $5 USD.  Even better cards may be available if your laptop uses a "half-height" card.

So what is the make/model of laptop?

Many laptops place the wireless card under a panel on the bottom of the laptop and replacing it is usually easy - a few screws, unclip the antenna wires, replace with new card.  Lots of demos on YouTube.  Sometimes the wireless card is under the keyboard and harder to get to.  Depends on the make/model.

---

### Post by jeremy31 on 2014-09-17
Some USB work after plugging them in and others like netgear need Win XP drivers and ndiswrapper to work and they don't seem to work well even then.  I do have a 7 year old USB wifi adapter that works great with 14.04, it only does a, b, and g speed but it is plug and play

I would recommend getting an Intel(not 7260 dual-band AC) or an Atheros PCI(e) over USB as it is easy to break anything external to a pc

---

### Post by manish_singh2 on 2014-09-17
My Laptop is dell vostro 2520 and it is an year old. Yes the wifi worked sometimes in ubuntu and also in kali after doing much of a mess. But I am not just interested in web browsing, I want to try out the hacking thing, so i thought of starting with **aircrack-ng** and after spending weeks in searching a fix for this problem i am done. 

A USB Wireless card or replacing can the inner can do me good. But what's better

---

### Post by weatherman2 on 2014-09-17
OK, then you can probably put almost any half height mini-PCI Express wireless card in the internal slot and it should work.  However, don't get a card designed for Lenovo or HP or you may have issues if you use Windows again.  You don't have to get a "Dell" card.  

I have had good luck with the Intel 6235 internal wireless card (rev 24) - dual band wireless + bluetooth.  In the US I can get them sometimes as cheap as $10 USD via eBay.  I have had issues with "new" cards from China or Hong Kong however - sometimes not as marked, so I stay away from them and get used cards.  The Intel 5100 is a slightly older card that will cost less.  Get the half-height card for your laptop most likely.  Again stay away from cards designed for HP or Lenovo.  You can double check the height requirement (half height or full height card) by finding the existing card or looking in the service manual if Dell provides one online.  Figure out how easy/hard it is to get to your wireless card too.  If it's not simple to access you might reconsider replacing it.

---

### Post by QIII on 2014-09-17
Hello!

We don't support queries about hacking, cracking, pen testing, aircrack, etc., on the forums.

You'll have to get help with that on another forum.  

Thread closed.

If you care to start a new thread dealing specifically and only with getting your wireless to work, you are perfectly welcome to do so.

---

