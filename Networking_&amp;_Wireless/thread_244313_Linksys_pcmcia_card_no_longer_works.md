---
title: "Linksys pcmcia card no longer works"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by umarc on 2006-08-26
I've an old Compaq Presario 1275 laptop I hadn't turned on in a while. Last night when I turned it on, it said I had 98 updates to install. After installing them, it asked me to reboot. After rebooting, my Linksys Etherfast 10/100 pcmcia card is no longer detected.

On the chance that something might have happened to the card, I tried replacing it with an identical spare. That card isn't recognized either.

When I type: cardctl ident

I see:

Socket 0:
  product info: "Linksys", "Ethe&#1076;
                                 "
  manfid: 0x0149, 0xc1ab
Socket 1:
  no product info available

Is that what I should be seeing?

Is anyone else having this type of problem?

Thanks,


umar

---

### Post by umarc on 2006-08-26
I got it working again by adding the following lines to /etc/pcmcia/config:

card "Linksys Ethe^A^CÔ
"
  manfid 0x0149, 0xc1ab
  bind "pcnet_cs"


umar

---

