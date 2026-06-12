---
title: "Experienced user stuck - Cell or Access Point: Invalid"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by waster on 2007-03-24
I am competent in setting up bcm43xx and ndiswrapper which I have done under Feisty. But...

With bcm43xx, I can set up the network at one end fine, but after a minute or two under ad-hoc networking , iwconfig reveals that the Cell (or AP) are invalid. This is accompanied by a reversion from ad-hoc to managed. I have disabled network manager. This is only half of the problem...

At the other end on my laptop, I have a netgear 11mb pcmcia card (orinoco driver) which cannot connect ad-hoc to the broadcom piece of crap. Ndiswrapper on the broadcom end is no good because it is stuck in 54g mode.

iwpriv eth1 network_mode b

fails under ndiswrapper. bcm43xx looks like it should be supporting 802.11b/g, according to iwconfig. N.b. I have had both cards working fine in maanged mode. And under Edgy, I had them working with each other in Ad-Hoc mode.

Please can someone help? Is Ad-Hoc just flaky regardless of the drivers?

---

