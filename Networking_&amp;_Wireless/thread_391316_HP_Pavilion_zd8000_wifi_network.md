---
title: "HP Pavilion zd8000 wifi network"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by whiteniko on 2007-03-23
Need help getting ubuntu to recognize the built-in wifi card

---

### Post by chili555 on 2007-03-23
Not much to go on here...

Please do the following in a terminal:```
lspci -v | less
```The 'less' part allows you to scroll back and forth until you find the wireless card; a Broadcom, maybe?

The listing will be detailed enough that you can see if its a Broadcom BCM43xyz or whatever. Since they are so common, there will be dozens of posts here detailing how to get it going. Just search the wireless forum for bcm43<whatever_yours_is>

---

