---
title: "wg111v2 + ndiswrapper + no scan results"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by darkphoenix16 on 2006-07-26
Hi everyone.

I have ndiswrapper-util(1.8) installed and 2.6.15-26 686 kernel. I have a wg111v2 wireless usb dongle with a rtl8187L chip.  The native drivers lock up my system on operations such as posting in message boards, sending email, etc... so I am trying out ndiswrapper out.  Others have reported success.

I used the 1.3.0 drivers from the realtek website.  They installed with ndiswrapper fine and it also detect my hardware.  The problem is that I cannot pick any signal up.  The scan will return nothing.

I have read that maybe the radio isn't on...but how would I go about turning it on?  ALso, maybe I am using a bad version of the wg111 drivers, or perhaps I should build ndiswrapper from source. Any help would be appreciated.

Other notes:
I have r8187 blacklisted
I can see the card with ifconfig as wlan0


thanks,
colin

---

