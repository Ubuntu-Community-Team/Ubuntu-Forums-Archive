---
title: "IS this card supported? (Ubiquiti 300mW atheros chipset)"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by tee2 on 2006-11-27
Hi I was wondering if [this]("http://www.ubnt.com/super_range_cardbus.php4") card was supported. It's an atheros chipset so I think it is but I just wanted to make sure before I buy it.

Thanks.

---

### Post by FrodoB on 2006-11-27
It looks like it should, but as they say, your mileage may vary. 

If you are using Dapper Drake or Edgy Eft from the regular install CD it should work out of the box and if you use the Alternate CD you will have to install the linux-restricted-modules for your kernel.

Let us know if it indeed works for you.

---

### Post by tee2 on 2006-11-27
bump in case anyone has tried this card before i buy it.

---

### Post by FrodoB on 2006-11-27
How much does it cost?

---

### Post by mfazed on 2006-12-06
I am using this card right now.  The madwifi driver is included in the restricted modules, so it should pretty much 'just work', but I have been having an issue where I have to force the speed  (sudo iwconfig ath0 rate 11M), or it just keeps hopping between a and b/g frequencies.

---

### Post by scottylans on 2006-12-07
Tee2,

If you're buying it from that Ebay guy, I can recommend him - the one who sells them for 129$ a pop.

I picked up the Orinoco model he sells with the little aerial and it works a damn charm for wardriving.

I was thinking of upgrading to the Ubiquiti - it sounds like a powerful card but I like you also want full support under Ubuntu (hassle free, not fiddly like ipw2200 used to be!)

The Orinico gold DOES work flawlessly under Ubuntu / Windows.

Let me know how you go.

---

### Post by tturrisi on 2006-12-08
This is where I get my cards:
[http://www.data-alliance.net/servlet/StoreFront](http://www.data-alliance.net/servlet/StoreFront)
shipping is fast & he's honest.  He also will respond to your email.  I use the Proxim:
[http://www.data-alliance.net/servlet/the-35/NEW-ORiNOCO-Gold-802.11G-fdsh-B/Detail](http://www.data-alliance.net/servlet/the-35/NEW-ORiNOCO-Gold-802.11G-fdsh-B/Detail)

---

### Post by scottylans on 2006-12-19
> **tee2 said:**
> Hi I was wondering if [this]("http://www.ubnt.com/super_range_cardbus.php4") card was supported. It's an atheros chipset so I think it is but I just wanted to make sure before I buy it.

Thanks.


Tee2, did you pick up the Ubiquiti and if so how is it for wardriving etc?

---

### Post by honeydew on 2006-12-20
I have this card and it worked great with dapper, I have not tested it in edgy yet though.  And yes it was awesome for wardriving =]

---

### Post by tturrisi on 2006-12-20
I was considering getting that card but after somemore research I decided to not get it.  Reason being that the 300mW is transmit power only, thus it won't make much differerence for war driving ot detecting more wlans if use kismet.  When a card is in rfmon (monitor mode) there is NO transmitting taking place, ONLY listening.  It will make a difference in windows using netstumbler though because windows drivers for wifi cards don't use rfmon mode.  Also, to really take advantage of that much transmit power you need a matched up antenna.  I have the antennas but think I could spend my $ better on other stuff.

---

### Post by scottylans on 2007-01-04
> **honeydew said:**
> I have this card and it worked great with dapper, I have not tested it in edgy yet though.  And yes it was awesome for wardriving =]

Honeydew,

How is the signal? I've got the orinoco with a single aerial port and it still seems fairly good but I was hoping to get something AWESOME.

Does it have good support in backtracker and other OS's ? Do you know what the actual chipset is?

---

### Post by scottylans on 2007-01-04
> **tturrisi said:**
> I was considering getting that card but after somemore research I decided to not get it.  Reason being that the 300mW is transmit power only, thus it won't make much differerence for war driving ot detecting more wlans if use kismet.  When a card is in rfmon (monitor mode) there is NO transmitting taking place, ONLY listening.  It will make a difference in windows using netstumbler though because windows drivers for wifi cards don't use rfmon mode.  Also, to really take advantage of that much transmit power you need a matched up antenna.  I have the antennas but think I could spend my $ better on other stuff.


tturrisi:

Thank you very much for this response, it's very informative!
How do you check these specifications and where?

I currently have this one:
[http://cgi.ebay.com.au/ORiNOCO-Gold-802-11G-B-Wireless-Card-WiFi-Antenna-Jack_W0QQitemZ290066497495QQihZ019QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItem](http://cgi.ebay.com.au/ORiNOCO-Gold-802-11G-B-Wireless-Card-WiFi-Antenna-Jack_W0QQitemZ290066497495QQihZ019QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItem)

This chat is about this one:
[http://cgi.ebay.com.au/Ubiquiti-300mW-Wireless-Card-802-11g-b-a-Antenna-Jacks_W0QQitemZ290067441253QQihZ019QQcategoryZ45000QQrdZ1QQcmdZViewItem](http://cgi.ebay.com.au/Ubiquiti-300mW-Wireless-Card-802-11g-b-a-Antenna-Jacks_W0QQitemZ290067441253QQihZ019QQcategoryZ45000QQrdZ1QQcmdZViewItem)

So they will likely be the same in quality?
I thought you could get hacked drivers for madwifi or atheros or something which allow packet injection while in monitor mode?

Would money be better spent on an aerial?

---

### Post by tturrisi on 2007-01-04
I'm not sure which is better,I don't ever do packet injection.  You'd likely get your answers at wardriving forums.

---

### Post by punkrokk on 2007-08-08
Hey,

I started using the Ubiquiti 300mw card with backtrack, and now I have switched my desktop to Ubuntu and it works fine. Sometimes I have a few hiccups, but other than that, it works great with mad wifi. Great range also :)

---

