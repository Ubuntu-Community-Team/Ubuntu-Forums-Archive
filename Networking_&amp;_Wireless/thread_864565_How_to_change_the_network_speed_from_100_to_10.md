---
title: "How to change the network speed from 100 to 10?"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by jakeconnor on 2008-07-19
My internet cable from the router is over 60 feet.
I know when I had windows installed the setting for the network card had to be changed from 100 to 10.

Where and how do you do this in Ubuntu's latest version for the network card.
I am just a beginner.

---

### Post by steveneddy on 2008-07-19
The speed will change automatically when it is necessary.

The maximum length for Ethernet before noticeable signal degradation is 150 feet.

---

### Post by jakeconnor on 2008-07-19
> **steveneddy said:**
> The speed will change automatically when it is necessary.

The maximum length for Ethernet before noticeable signal degradation is 150 feet.

Well I know is that under windows that I have to change the setting from 100 to 10 for the internet to work.


So my question is under Ubuntu where do you change the setting from?
I have spent 2 hours trying to find the setting under Unbuntu and cannot find where it is.

---

### Post by steveneddy on 2008-07-19
> **jakeconnor said:**
> Well I know is that under windows that I have to change the setting from 100 to 10 for the internet to work.


So my question is under Ubuntu where do you change the setting from?
I have spent 2 hours trying to find the setting under Unbuntu and cannot find where it is.

I don't know.

I also don't believe it is necessary unless you have very old networking equipment upstream of this PC.

---

### Post by lswb on 2008-07-19
It can be done with the command

sudo ethtool speed 10

However, for proper cabling, both 10Mbps and 100Mbps ethernet can have a maximum length of up to 100 meters. The "up to" is because not everything is perfect. While the slower speed is more tolerant of adverse conditions than 100Mbs, it may not really be necessary for you to change to the lower speed. OTOH if the cable is going from your computer to a DSL or cable modem there is probably substantially less than 10Mbs of bandwidth available anyway.

---

