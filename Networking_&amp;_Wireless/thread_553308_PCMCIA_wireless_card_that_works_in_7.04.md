---
title: "PCMCIA wireless card that works in 7.04"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Vadi on 2007-09-17
Can anyone recommend me a wireless card that for sure works out of the box in Fiesty?

I've read a ton of threads, read the wiki compatibility guide (which unfortunately is useless, as there are very few entries for 7.04, and as I learnt, newer version of Ubuntu actually tend to worsen the wireless in some cases).

I had a whole list of cards, but after reading various threads, pretty much all of them are checked off now. Bah :(

I just need a wireless card that supports b, g protocols, has a good range, and costs under $200. And works flawlessly in my Ubuntu.

Someone recommend some please?

---

### Post by reckless2k2 on 2007-09-17
i believe in the community wiki they show a list of out of the box supported cards.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by Vadi on 2007-09-17
> **Vadi said:**
> ...read the wiki compatibility guide (which unfortunately is useless, as there are very few entries for 7.04, and as I learnt, newer version of Ubuntu actually tend to worsen the wireless in some cases)...

I already did, thanks. I didn't find it useful at all.

---

### Post by Junglizer on 2007-09-17
Sure thing. though I think the whole "under $200 dollars" is a little high. I've got all sorts of cards that I'd suggest that are in the 130-180 range =)

[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500#]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500#") See if you can find that card locally, and look on the box to see its version number, or buy it, keep the recipt. The version (5) that I have of that card is an Atheros chip and it works excellently.  In the upper price range check out the Ubiquity Super Range Cardbus:[http://www.ubnt.com/products_src.php4]("http://www.ubnt.com/products_src.php4")
Under their "where to buy" page vendors are avalible, I bought mine from Microm Technologies. Good site. Thats a bit more expensive, dual-band, no external antenna, and about $130. Though it IS an Atheros 5212 chipset which works most-deff. 

Also, as far as "working with Ubuntu" I can only give my knowledge of gettin these cards to work using the Madwifi ([http://www.madwifi.org]("http://www.madwifi.org")) drivers. The easiest way is to download the source. (tar.bz2 or tar.gz file) then run the following, either sudo or as root:
[I]tar xvf madwifi.tar.gz
cd madwifi
make
make install
cd ..
rm -f madwif.tar.gz
rm -rf madwifi[/I]
then you'd also have to have the "wireless tools" installed, but i'm 99% positive that is included in Ubuntu's default load.

---

### Post by reckless2k2 on 2007-09-17
yeah you can get atheros chipset for like $50 maybe.

---

### Post by Vadi on 2007-09-17
Hm. That ubiquity card - does it support linux? I only saw windows on it's page, and that vendor isn't even listed in the docs.

I'll look into the Belkin card, thanks :)

---

### Post by Junglizer on 2007-09-17
Yes, it works in Linux as well as supported by OpenBSD's "ath" driver. As far as the debate on that, is that its the 5213 chipset which reports to the OS as 5212 which is supported. I have both of the cards I listed. Though unless you are going to be doing a lot with wireless, I would try and dissuade you from purchasing the Ubiquity, just b/c it is expensive and not at all what you should use for general connections. It is 300mWs which will significantly decrease your battery life also. You must use an external antenna also. 

... The vendor isn't listed in the doc's b/c they are very badass. Heh. I looked into it quite a bit before purchasing.

---

### Post by Vadi on 2007-09-17
Okay. I've looked up that Belkin card, going to see how that works out... buying via paypal to canada is a pain!

---

### Post by Vadi on 2007-09-18
Okay, waiting on a few email replies from a bunch of possible vendors, but meanwhile, just for shits and giggles, I sent this email off to Belkin:
[U]
Hello,

I'm interested in the Wireless G Notebook Card, part # F5D7010. I've had my friends recommend it for it's excellent range and good encryption. However, the website says that it only works with Microsoft Operating System - I myself am on Ubuntu 7.04, a free and an open-source operating system. Is the card compatible with my preferred OS?

Thank you for your time.[/U]

Let's see what they reply!

---

### Post by Junglizer on 2007-09-18
They will tell you no, as will most manufactures. However they may say yes, some companies slap the "linux compatible device" right on the box. This simply means that it works in linux. Which linux, which drivers, how much work is not taken into account. The "Linux compatible device" is a joke really. It always makes me laugh at least. I would see what they say, and if nothing else, try to find out what version the card is. Mine is a version 5, then you can google **F5D7010 v5 chipset** and get your answer pretty quickly. If it is an Atheros check [this page]("http://madwifi.org/wiki/Compatibility/Atheros"). If its not listed it may still work, but I'd put some serious thought into buying it if its not on there.

---

### Post by Vadi on 2007-09-18
I don't know what version is it, I'll check it out, moment.

---

### Post by Vadi on 2007-09-18
I don't think it says what version anywhere.

Here's the site I'm looking at ([click]("http://www.provantage.com/belkin-f5d7010~7BELR009.htm"))

---

### Post by Vadi on 2007-09-18
Oh wow...

Look at [this]("http://www.provantage.com/belkin-f5d7011~7BELR00M.htm") card. Someone even said it works on their Ubuntu!

---

### Post by Junglizer on 2007-09-18
Eww.. That last one is using Broadcom. Yes I'm aware that they are easier to work with now, but labeling them as the devil for such a long period of time is hard to go back on. Besides, I'm not sure how well FULL functionality with them is. 

I'm also one to avoid all of that "speed-booster" crap, as its not really going to help you unless...
A) You're transmitting large quantities of large files via WLAN.
B) Your router is similar model and has same capabilities. 
C) You're paying enough per month to your ISP to really make it worth the extra money per card, otherwise you just get stuck in the bottleneck. What good is a gigabit card, running over CAT5 hooked up to 5meg DSL?

---

### Post by Vadi on 2007-09-18
Heh, true.

Trying to get the first card still meanwhile... the site says they accept paypal, but apparently not from "international" customers yet (canada here...).

Bah.

---

### Post by Junglizer on 2007-09-21
Any news on this? Were they kind enough to respond back?

---

### Post by Vadi on 2007-09-21
Newp, nothing from Belkin yet.

I ordered a card yesterday from a quebec company, it should be on it's way. Either today, or Monday is should be here :)

---

### Post by Vadi on 2007-09-27
... well, I got the card. After prying it out of the mailbox with a knife, because it barely fit there and got stuck, I plugged it into the laptop... and nada. iwconfig doesn't even see it. Feh :|

---

### Post by Vadi on 2007-09-27
Apparently I got the v7, not the v5 like you. But, I followed the instructions from the wiki - "Need ndiswapper-utils and the Realtek Windows driver (net8185.inf). After installing drive, need to use ndiswrapper -a command to link the driver to the card. Otherwise follow ndiswrapper install instructions. Tested in Feisty.", and got it working! Hah.

I'll just post better ones, as those ones aren't that clear.

---

