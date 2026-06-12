---
title: "No internet working at all!"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by evadwolrab on 2008-04-24
When I plug in to my router via ethernet cable, it tries to acquire an IP for ages then gives up.

I've tried going to the restricted drivers dialog, I click enable on the Broadcom 43 wireless drivers and it goes online to try to find it. Obviously it fails since wired internet won't even work. This wasn't a problem in Gutsy, as I just downloaded the drivers and firmware on another computer and pointed the drivers dialog at them. But it seems, since I upgraded to Hardy earlier today, that there is no longer the option to look for the file locally, it just tries to go online and says it's failed, then takes you back to the drivers dialog.

Any clues? :popcorn:

---

### Post by yghannam7388 on 2008-04-24
I had a similar problem when I upgraded to Hardy. The network manager kept assigning the wrong ip with my wireless network. To get it to work I had to set up the network manually. I used the tutorial in this forum. Give that a try, it doesn't take too long to do.

P.S. I have a Broadcom/Intel wireless adapter and when you set up the network you have to use "wext" as the driver because the Broadcom/Intel drivers are old, according to the manual.

---

### Post by Patsoe on 2008-04-24
I'm not sure why your wired ethernet connection would not work. Is the router configured with the wired ports enabled?

As for the b43 driver, check this thread: [http://ubuntuforums.org/showthread.php?t=763995](http://ubuntuforums.org/showthread.php?t=763995)
and especially post #8 that tells you which firmware to download.

---

