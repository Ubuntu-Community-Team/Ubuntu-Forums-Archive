---
title: "Wifi Trouble on Acer Aspire 4720Z. Noob need help!"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by SyntaxMage on 2008-08-08
Alright. I installed Linux Ubuntu 8.4 a while back and have been struggling with everything for a while, but I finally have EVERYTHING working for me EXCEPT for the wireless. I've tried almost everything I can find on the forums and nothing is seeming to help. it's all too user specific, so I figured I'd do a user specific post. I have an Acer Aspire 4720Z, and I know it has an intel chipset for the processor and graphics, but other than that I don't know how to check specs (maybe i'm just tired or absent minded tonight). I need help, it's the one thing I haven't found a fix for. Can anybody help me?

---

### Post by rmjesse on 2009-05-02
My Acer Aspire 4720Z has a Atheros AR5007EG, but to check, just do lspci on the command line.  Better yet, lspci | grep -i wireless will probably get it without having to read thru a huge list of hardware.

For the wireless, I finally got mine to work with the madwifi driver.  It's proprietary, but works.  Here's an article for how to get it in jaunty:
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

