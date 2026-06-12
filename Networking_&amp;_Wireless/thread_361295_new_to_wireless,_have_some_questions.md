---
title: "new to wireless, have some questions"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by potrick on 2007-02-14
Hello everyone. Long time luker, occasional poster, love the community. 
  Anyway, on to the issue at hand. I just bought a beautiful Dell Latitude D400, used. It didn't come with a wireless card, so now I'm wondering if there is a certain brand or make of wireless care I can buy to ensure that getting it to work with Ubuntu will be as simple as possible. Are there any suggestions? I'm happily living the wired life for now, I'd just like to be as informed as possible before I make any purchases. 
  Thanks for taking the time to read this.

---

### Post by bg1256 on 2007-02-14
You might try searching the forums for various brands you are considering.  If you see a brand that has had a lot of success, then maybe you should go with that one.

---

### Post by potrick on 2007-02-14
Sounds like a good idea, I'll do that.

If anyone reading has a brand they'd like to recommend, I'd love to hear from you.

---

### Post by gradedcheese on 2007-02-14
The trick is to buy a regular card, not one that advertises extra features like "pre N" or various marketing phrases ("turbo" ...whatever).  I have a cheapo Belkin with the Atheros chipset that works great, but fancier Belkin cards have whacky newer chipsets that are not documented.  The other trick is to buy from a store that has a good return policy.  The store I buy from has 14 days returns, even on opened-box items, no questions asked.  I then just pick any card I want, try it, and if it doesn't work, I return it and pick another (let th vendor eat the restocking cost for having a bad chipset).  

The reason for this is that vendors change chipsets all the time, so you can't be 100% sure that the card you're buying still has the right chipset.  I find it easier to just pick nearly at random and then run 'lspci' to see what I have :)  Classic example: Netgear '511 cards.  They worked great (Prism chipset), then suddenly Netgear switched to Marvell's chipset, the product box did not change but the card won't work anymore.

That said, I've been (I think) about 90% lucky getting cards that work the first time.  Also, I don't settle for ndiswrapper (ie: a wrapper that allows the Windows driver to be used).  If there's no proper Linux driver, I don't use the card.

---

