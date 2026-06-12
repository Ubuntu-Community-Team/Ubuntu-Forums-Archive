---
title: "Not a newbie, but still stumped- Belkin F5D7010 v6000"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by johnzbesko on 2006-07-31
I have tried both the rt61 native driver and the ndiswrapper approach to getting my new Belkin pcmcia F5D7010 to work, but no luck.

I've used the native driver downloaded from:

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

as well as the firmware. I also tried ndiswrapper, using the drivers from the Windows cdrom that came packaged with the card. I blacklisted the rt61 driver when trying the ndiswrapper.

Either way, the device is detected (either ra0 or wlan0) and I can:

iwconfig [ra0 or wlan0] key [hex key]

But I cannot:

iwconfig [ra0, wlan0] essid "ZBESKO"

(it doesn't "stick", some variations of what I tried even produced segfault or hung the terminal.)

No wireless signal is detected, "dhclient [ra0, wlan0]" produces no offers.

It works in Windows, so I know the card is OK.

I'm stumped. /var/log/messages seems to imply everything is fine, too.

I'm guessing that the firmware is not being loaded. Where does it go?

What else can I try?

---

### Post by Fitzcarraldo on 2006-10-07
Maybe the procedure in the following thread might be of help:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

