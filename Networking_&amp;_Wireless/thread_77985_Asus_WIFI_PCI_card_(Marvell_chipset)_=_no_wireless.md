---
title: "Asus WIFI PCI card (Marvell chipset) = no wireless extension"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by pawdk on 2005-10-17
hi there.

my first post is a cry for help, positive wibes all around :) I finally managed to get Ubuntu 5.10 installed (buggy CD?), fixed the root hostfile problem i had, now there's just one thing missing. my wireless internet access...

the device is present in the device manager, but there's no wlan extension to activate... :( I can only see the loopback & LAN extensions.

I've read through a lot of topics, but nothing seemed to match my specific problem... maybe it's the eyes of the Linux noob that are to blame? :???:

UPDATE: Nevermind, fixed it thanks to a previous post in the forum... :)

---

### Post by skunkydog on 2005-10-26
hi,

did you end up using ndiswrapper?  i recently got a new wifi card (Encore ENPWI-G-RLAM) with a marvell chipset, old one was a rt2500 chipset  (but also Encore ENPWI-G-RLAM) and had a linux driver, which let me use it with kismet and airsnort.  i'm trying to find a native driver for this new chipset but haven't found much. i would be content to find something definitive that says there is no native driver.

if you didn't use ndiswrapper, could you give me a link to what ever doc you used?

thanks

---

### Post by Mr. Picklesworth on 2006-03-12
Hi...
I'm having the same difficulty as you getting my ASUS Wifi card working with Ubuntu, and I also can't find the thread you're talking about.
So... if you somehow remember what thread it is, could you please point me to it?
Looking at the startup screen, I can see that the card is detected, etc. by Ubuntu, but I have no clue how to configure it and all that.

Thanks in advance!

Edit:
Then I realized that there's a whole section with these questions :P
I may still need help, so may as well not delete this... but sorry if the question is already answered on the same page of threads as this one.


Edit2:
Okay... I think I solved it.
For anyone else having problems, this is how I sorted it out...
Install the ndiswrapper package, which should be on your install CD.
Follow the directions here: [http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)
Bye :)

---

