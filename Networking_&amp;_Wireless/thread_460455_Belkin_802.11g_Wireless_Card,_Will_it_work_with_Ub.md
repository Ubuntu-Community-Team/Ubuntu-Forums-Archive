---
title: "Belkin 802.11g Wireless Card, Will it work with Ubuntu?"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by beng120 on 2007-05-31
Hi everyone,
I'm thinking about switching to ubuntu and need to know if my wireless card will work with the latest version of ubuntu, 7.04. I have a Belkin 802.11g Wireless Card, product code FSD7000 or FSD7001. I'm not sure which of the 2 as i'm not quite certain if i have the basic card or the plus.
Does anyone know if it will work, and if so the relevant drivers i will need to install it, and how i go about it.

Thanks in advance =]

---

### Post by spd106 on 2007-06-01
The place to look is in the Device Manager. There you can find the Wifi Controller chip version. 

If you find it is a BCM43xx then you can use the bcm43xx driver by downloading the firmware through the bcm43xx-fwcutter package or you can use ndiswrapper. Both have there advantages, at the moment ndiswrapper is favoured, but the native driver is a better long term solution.

If you find it's a Ralink device then it should work out of the box, if not try searching the forum for the version it says.

---

