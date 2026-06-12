---
title: "1000 Mbps Ethernet PCI Card"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Glkanter on 2011-07-27
I just installed this card: Gigabit Ethernet PCI Card into my PC.

The green light indicates it's operating in the 10/100 Mbps mode.

The included CD seems like it's only for Windows.

I downloaded the [ST1000BT32.zip]("http://c531238.r38.cf2.rackcdn.com/ProductDrivers/ST1000BT32.zip") file from [http://www.startech.com/Networking-IO/Adapter-Cards/10100-1000-Mbps-32-bit-PCI-Gigabit-Ethernet-Card~ST1000BT32#dnlds]("http://www.startech.com/Networking-IO/Adapter-Cards/10100-1000-Mbps-32-bit-PCI-Gigabit-Ethernet-Card%7EST1000BT32#dnlds").

I think I've unzipped it.

There's a Linus folder.

Pretty much, at this point I'm lost.

I welcome any help in configuring this card to the 1000 Mbps.

Thanks!

---

### Post by alphacrucis2 on 2011-07-27
> **Glkanter said:**
> I just installed this card: Gigabit Ethernet PCI Card into my PC.

The green light indicates it's operating in the 10/100 Mbps mode.

The included CD seems like it's only for Windows.

I downloaded the [ST1000BT32.zip]("http://c531238.r38.cf2.rackcdn.com/ProductDrivers/ST1000BT32.zip") file from [http://www.startech.com/Networking-IO/Adapter-Cards/10100-1000-Mbps-32-bit-PCI-Gigabit-Ethernet-Card~ST1000BT32#dnlds]("http://www.startech.com/Networking-IO/Adapter-Cards/10100-1000-Mbps-32-bit-PCI-Gigabit-Ethernet-Card%7EST1000BT32#dnlds").

I think I've unzipped it.

There's a Linus folder.

Pretty much, at this point I'm lost.

I welcome any help in configuring this card to the 1000 Mbps.

Thanks!

Is the switch or other device it is connected to capable of gigabit operation? If not then it will negotiate the lowest common demoninator. You may also want to check the cable. Gigabit ethernet requires all eight wires in the cable to be connected whereas 10/100 mbps only use two pairs.

---

### Post by Glkanter on 2011-07-28
Thanks!

My router only goes to 100 Mbps.
 
 [http://www.zoomtel.com/products/glan_overview.html#4501](http://www.zoomtel.com/products/glan_overview.html#4501) - Model #4402


A friend of mine gave me the card, somehow he had an extra. He *raved* about the difference it made.

I just sent him an e-mail suggesting that maybe he had been at 10 Mbps before, and now he's seeing 100 Mbp, not 1000 Mbps.

I guess I should close the thread.

---

