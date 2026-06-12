---
title: "[SOLVED] Recommended Card for Wireless Roaming in ubuntu 7.04"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by crjackson on 2007-08-21
My wife's sony laptop had an intel wireless g card that just died (internal).  

I'm looking to replace the card and it looks like PCMCIA cardbus or whatever you call the type that plugs into the side slot is probably what I'll go with.

She runs XP right now, but I plan to install ubuntu 7.04.  I've found a couple of cards that seem to be linux freindly but I want to know if roaming will work.  My wife is in collage and connects to many different networks so this is a must.  I'm looking at these..

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105")

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127116]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127116")

Thanks for any advice...

---

### Post by kevdog on 2007-08-21
Side note -- glad to see all the comments from the Linux users on NewEgg -- way to go -- Wow!!

Anyway -- I think if I had a choice I would probably go with #2 even though it is more expensive.

Reasoning -- Again with any wireless card and Ubuntu, I really dont care who makes the card, rather than the chipset that is inside.  The first has a ra chipset that uses the rt2500 driver - which would require with gusty, or feisty installation of the serial monkey rt2500 drivers (sound familiar).  Again for a GUI you would uses either rutilt (like you set up) or wicd -- but not the default network manager.  If you want to save a few bucks but spend some time setting up the serial monkey drivers (5-10 minutes if you know how to do it, then it would be a good buy)

Card #2 uses an Atheros chipset -- which according to the comments has a much higher likelihood of working "out of the box" than card #1.  The madwifi drivers are integrated (under restricted drivers) into feisty, so likely if the restricted drivers are installed, no further configuration would be necessary (unless you wanted wpa which would require the wpa-supplicant installation (the same with both cards)).

As far as performance, they are probably the same so I wouldnt let that stand in your way.

The slot you want to stick the card into is known as the PCMCIA (PC mini card interface adapter -- I think that is what it stands for at least :)).

Any more questions just let me know.

---

### Post by crjackson on 2007-08-22
> **kevdog said:**
> Side note -- glad to see all the comments from the Linux users on NewEgg -- way to go -- Wow!!

Anyway -- I think if I had a choice I would probably go with #2 even though it is more expensive.

Reasoning -- Again with any wireless card and Ubuntu, I really dont care who makes the card, rather than the chipset that is inside.  The first has a ra chipset that uses the rt2500 driver - which would require with gusty, or feisty installation of the serial monkey rt2500 drivers (sound familiar).  Again for a GUI you would uses either rutilt (like you set up) or wicd -- but not the default network manager.  If you want to save a few bucks but spend some time setting up the serial monkey drivers (5-10 minutes if you know how to do it, then it would be a good buy)

Card #2 uses an Atheros chipset -- which according to the comments has a much higher likelihood of working "out of the box" than card #1.  The madwifi drivers are integrated (under restricted drivers) into feisty, so likely if the restricted drivers are installed, no further configuration would be necessary (unless you wanted wpa which would require the wpa-supplicant installation (the same with both cards)).

As far as performance, they are probably the same so I wouldnt let that stand in your way.

The slot you want to stick the card into is known as the PCMCIA (PC mini card interface adapter -- I think that is what it stands for at least :)).

Any more questions just let me know.

I'm looking for the ability to change wifi networks on the fly.  Idea would be to click on network manager and select network signal in range and connect.

My wife needs this ability so that she can connect at school / home / book store.

If I go with card 2 is this something that would be supported.  Using the seamonkey driver install (as on one of my home machines) this isn't possible as far as I can tell.  It doesn't see any other networks.

---

### Post by crjackson on 2007-08-22
> **crjackson said:**
> I'm looking for the ability to change wifi networks on the fly.  Idea would be to click on network manager and select network signal in range and connect.

My wife needs this ability so that she can connect at school / home / book store.

If I go with card 2 is this something that would be supported.  Using the seamonkey driver install (as on one of my home machines) this isn't possible as far as I can tell.  It doesn't see any other networks.

kevdog, I want to order this thing right away.  Do you know if this 2nd setup would support the ability to see other wireless networks and connect on the fly?  I need roaming...  Does the mad wifi driver support this?

---

### Post by Wharf Rat on 2007-08-22
I had all sorts of trouble with my Airlink card. I found a SMC card in my junk box and planned on installing it. Almost as soon as I inserted the SMC card, Ubuntu detected it and loaded drivers.

No issues.   
Look at SMC.

---

### Post by crjackson on 2007-12-01
I wound up getting this card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320105")

I must say I'm really impressed.  It works great right out of the box...

---

### Post by kevdog on 2007-12-02
Does that card have an Atheros chipset??  Ill recommend this card to others based on your experience.

---

### Post by crjackson on 2008-01-27
> **kevdog said:**
> Does that card have an Atheros chipset??  Ill recommend this card to others based on your experience.

Wow, I couldn't find this thread for a long time.  Here's the info:

```
 *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:60:d4:ec:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.106 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
charles@emachines-m6809:~$ 
```

---

### Post by kevdog on 2008-01-27
Hmm, 

glad that really worked for you.  I know other have had some bad experiences with the rt2500 drivers in gutsy.  It works for some but not others.  I dont know if that means its a driver problem or "user" problem.

---

### Post by rustybronco on 2008-01-27
One of the cheepest dang cards I bought was a best-by Dynex dx-wgnbc and it has been the most dependable pcmcia card yet.
yes it has an atheros chipset....
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

```
[http://ubuntuhcl.org/pub/reviews.php?product_id=410](http://ubuntuhcl.org/pub/reviews.php?product_id=410)

---

### Post by kevdog on 2008-01-27
crjackson

I just ordered that card.  So thanks.  I was looking for a pci ra chipset.  The thing that makes me really angry with newegg, and product packaging for that matter, is that the chipset is not advertised on newegg or on the product boxes??  I really think this is deception on the part of the wireless card makers.

---

### Post by crjackson on 2008-01-27
> **kevdog said:**
> crjackson

I just ordered that card.  So thanks.  I was looking for a pci ra chipset.  The thing that makes me really angry with newegg, and product packaging for that matter, is that the chipset is not advertised on newegg or on the product boxes??  I really think this is deception on the part of the wireless card makers.

I ordered it based on the comments from others that it works in Ubuntu out of the box.  I was pleased with the product, but the specs page wasn't very helpful.

---

