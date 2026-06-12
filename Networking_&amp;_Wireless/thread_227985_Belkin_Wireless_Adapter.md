---
title: "Belkin Wireless Adapter"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by jasa2k6 on 2006-08-02
Iv got a Belkin F5D7050 802.11g 54 Mpbs USB wirless adapter..to use it you need the drivers(oviously) and it needs software to run..the software is in exe form...


1 last question....how do i run exe...i heard of wine but how do i install it..?

BTW Ubuntu ROCKS!

---

### Post by amp_man on 2006-08-02
DON'T try to use your windows drivers straight from an exe. if it were that easy, this forum wouldn't exist. Please post the output of "lsusb"

---

### Post by jasa2k6 on 2006-08-02
what you mean..sorry im a total n00b

---

### Post by weekend warrior on 2006-08-02
Check this thread
[http://www.ubuntuforums.org/showthread.php?t=219911&highlight=Belkin+F5D7050](http://www.ubuntuforums.org/showthread.php?t=219911&highlight=Belkin+F5D7050)
make sure you use the search function next time, yeah? ;) 

What amp_man means is open the Terminal or Konsole application, type lsusb then cut and paste here what it says.

Also, if you're completely new to Linux you may want to consider getting a fully supported adapter that will work right out of the box without needing anything from Windows. The ones on [this list from the Free Software Foundation]("http://www.fsf.org/resources/hw/net/wireless/cards.html") will do just that and they don't cost much, especially considering the time saved and/or frustration avoided.

HTH

---

### Post by jasa2k6 on 2006-08-14
ok but how do i get wine installed? i tried to but everytime it said something was outa date..

---

### Post by weekend warrior on 2006-08-14
You certainly don't need Wine, you may need Ndiswrapper. Did you read any of those links on the Belkin F5D7050?

Again jasa2k6, as I said - if this is totally new to you, I would **strongly** recommend getting a wireless device that "just works" out of the box. It will save you needless frustration. It's worth the investment.

If you want an exmple of what I'm talking about, read through [this thread]("http://ubuntuforums.org/showthread.php?t=234143").

Click on my signature below and you'll find models and versions that will work well for you.

---

### Post by asalford on 2006-08-14
see my howto on the usb belkin

[http://www.linuxquestions.org/questions/showthread.php?t=449166](http://www.linuxquestions.org/questions/showthread.php?t=449166)

it is very detailed and customized for ubuntu.

---

### Post by weekend warrior on 2006-08-14
So jasa2k6, it looks like there are a few ways to get this adapter going:

Using the Ralink drivers from their site as in asalford's howto

Using Ndiswrapper as directed [here]("http://www.ubuntuforums.org/showthread.php?t=210035")

Using the driver from the rt2x00 Open Source Project as mentioned [here]("http://www.ubuntuforums.org/showthread.php?t=231138&highlight=Belkin+F5D7050")

There are also some rt2500 packages already in the repositories that can be used.

This would depend I'd say on the version you have, which you haven't told us yet. I'd already assumed it wasn't the v2000 (which is a shame because) otherwise it would have probably "just worked". You need to give more information if you want help.

---

