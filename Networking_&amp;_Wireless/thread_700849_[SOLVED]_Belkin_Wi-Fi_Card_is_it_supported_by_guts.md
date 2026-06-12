---
title: "[SOLVED] Belkin Wi-Fi Card? is it supported by gutsy?"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by jmate24 on 2008-02-18
from what i have read in other posts it seem's that belkin is not a good candidate for ubuntu...sigh
but what other cards work well with gutsy? the hardware compatability list on the documentation site is just out of date and has a lot of missing info. i need one that will work for up to 100ft and be an either b or g 2.4Mhz adapter card but is there another way like a wireless receiver hub? so i can just plug my computers lan cable into it and it receives the signal and converts it into a wired connection?

---

### Post by mrsteveman1 on 2008-02-18
Actually belkin switches chipsets constantly, so some of their cards use atheros, some are ralink, i have a belkin USB stick with a zd1211b in it that works OK most of the time.

It all depends on the revision of each model. Linksys does the same thing, these companies change chipsets all the time.

The madwifi site has some exact model/revision numbers for specific cards that have atheros chipsets in them, which should probably be your goal if you have a choice.

You can in fact get a wireless bridge device, which just plugs into ethernet. Linksys makes some i know that for sure.

If you already have this belkin card, you should post the output of lspci so we know if it works in linux or not.

---

### Post by jmate24 on 2008-02-19
sorry i don't have the card... it was recommended to me by a friend.
so what chipset is the most supported by Ubuntu Gutsy 7.10
but the friend solely uses windows.
so a wireless receiver/ hub is my best bet but, i am leaning towards belkin because i hear it's more reliable. are there any more suggestions?:-|

---

### Post by rustybronco on 2008-02-19
[http://ubuntuhcl.org/pub/manufacturers.php?category_id=32](http://ubuntuhcl.org/pub/manufacturers.php?category_id=32)
plus  this one [http://ubuntuhcl.org/pub/reviews.php?product_id=503](http://ubuntuhcl.org/pub/reviews.php?product_id=503)
what kind of device are you looking for an internal pci, pci-e, pcmcia, usb ? is it for a  laptop, desktop ?

---

### Post by jmate24 on 2008-02-19
i am looking for a belkin wireless hub/router that can receive wireless signal and turn it in to wired and if possible repeat the wireless signal from my 2wire DSL modem i know that the networks that the modem support are b, b/g and possibly n.

---

### Post by jmate24 on 2008-02-24
and will that work with gutsy?

---

### Post by Mogurijin on 2008-02-25
It looks like to me you are looking for an Access Point. Do you just want to extend the reach of your router? Or are you switching from a wired set-up to a wireless one?

If the hardware isn't a component of the computer, I would think that the OS wouldn't cause to much issue. Now, a wireless NIC for your computer is a different story. You would probably want something that doesn't require ndiswrapper. Netgear (I know from experience) is kind of hit and miss on that.

From what little knowledge I know on this subject, Intel wireless NICs seem to be some of the better ones for Ubuntu. But I could be horribly wrong :oops:

---

### Post by jmate24 on 2008-03-10
an access point yes to receive signal and put it into wired connection but i have a friend whose had trouble with his access point taking over the network. and so i am not entirely sure that i want one and in my house we have 2 internet connections because of windows live one-care because my mom and brother use windows and i have clearewire so that i can use ubuntu instead of windows.

---

### Post by Mogurijin on 2008-03-12
Unfortunately, I'm not too skilled at these things. However, that being said, I have sort of messed with an access point before. From my experience they just show up as another wireless network, but connecting to them in turn grants you access to what it was plugged into (like a router). I'm guessing an access point should just look like another wired device to another piece of hardware (unless they are both bridging wireless connections). So  I hope that helps :(

---

### Post by jmate24 on 2008-03-17
thanks.

---

