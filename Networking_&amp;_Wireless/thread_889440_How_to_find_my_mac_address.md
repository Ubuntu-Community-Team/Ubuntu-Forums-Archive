---
title: "How to find my mac address"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Tlingit on 2008-08-14
ifconfig -a 


ethernet
HWaddr 00:00:00:00(example)

Ethernet 2
HWaddr 00:00:00:00(example)


Wireless card(<--Example name)

HWaddr 00-00-00-00-00-00(example)


Why does my wireless card mac look different? how do i find the right one or use this one. 

Is it true if there are an abundance amount of insignificant fig's zero's they may be omitted?

That is all i know and can find.

Thanks

---

### Post by MJN on 2008-08-14
That's very interesting and I think you're bang on the nail about omitting the most-significant bits if all zero. However, I must say I've not seen it done this way before - sure omitting leading zero within the 2-byte block (e.g. 0B becomes B, or 00 becomes 0) but not omitting entire 2-byte blocks to nothing.
 
So, given all MAC addresses are 6 bytes in length then your wireless MAC is spot on. One can only assume that your wired MAC has has its four leading zeros omitted. It doesn't help that you've not written the true values!!
 
Try looking up the first three bytes of your MAC addresses on [http://standards.ieee.org/regauth/oui/oui.txt](http://standards.ieee.org/regauth/oui/oui.txt) and comparing against the manufacturer of the card. Unless the card is a fake, or of otherwise equally dubious origin, then you should hopefully be able to work out what's going on.
 
Mathew

---

