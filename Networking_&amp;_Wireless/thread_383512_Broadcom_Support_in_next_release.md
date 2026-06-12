---
title: "Broadcom Support in next release?"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by max_power on 2007-03-13
Will Broadcom wireless cards work out of the box with the upcoming Ubuntu release? I use ubuntu on my desktop but with no (good) wireless support its just to frustrating on my laptop. Ive tried ndswrapper but its pretty buggy.

Thanks:guitar:

---

### Post by gradedcheese on 2007-03-13
The reason Broadcom is not supported has nothing to do with Ubuntu or Linux directly, and everything to do with Broadcom.  They, as a company, have a policy of not providing any documentation whatsoever on their chips, making it impossible for the community to write drivers for them.  So that's never going to change until their attitude changes.  In the mean time you can continue using the ndiswrapper hack or buy a card whose chipset is made by a company with a better reputation.  If you are interested, [here is more detail]("http://andrey.thedotcommune.com/wireless.html") on the matter (as I see it anyhow).

---

### Post by max_power on 2007-03-13
yeah i know about the propriatery issue, but i had heard that 3rd party support would be availible by enabling something and agreeing to a license form. i was wondering if that had any legs

---

### Post by gradedcheese on 2007-03-13
Ok, but a Broadcom driver does not exist, there's nothing to install even if you agreed to some nasty license.  The reason is that Broadcom hasn't written a driver, and the community cannot do it either until Broadcom's attitude changes.

Also please be aware that the moment you load a closed-sourced module, your kernel is tainted.  You should read about the implications of that if needed.  This also means things like the driver will not survive minor upgrades (until its maintainer bothers to recompile and roll you a new binary), and so on.  Also the driver will likely be buggy and no one in the community will be able to review it and fix things.  The driver quality will be pretty poor compared to a real open source driver such as what you'd get by using a supported WiFi card...

---

