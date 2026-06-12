---
title: "boot wireless laptop remotely through SSH"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by tomaasj on 2014-09-02
Anyone,

how to boot my laptop remotely ?

Setup:

[LIST=1]
[*]Laptop (Inspiron 6400, 12.04) is at home and powered up.
[*]
[*]It is connected wirelessly to the internet.
[*]
[*]The laptop is NOT connected with an ethernet cable to my ADSL modem.
[*]
[*]From my work computer I can get into my laptop using SSH.
[*]
[*]From my work computer I can shut it down.
[/LIST]

Is it possible to start up my laptop again using SSH ?


Tomaasj

---

### Post by weatherman2 on 2014-09-02
Yes, it is possible, but not in exactly the way you describe. You need to use a wireless ethernet bridge instead of the laptop's built-in wireless card.  Connect an ethernet cable from the laptop to the wireless bridge.  The wireless bridge connects wirelessly to your ADSL modem.

But you would use WOL (Wake-On-Lan) instead of ssh to wake up the laptop.  You could either connect to your home network via VPN, then issue the WOL magic packet to wake up your laptop that way, or connect remotely to your ADSL router and use that to issue WOL - but your router may not have the ability to do WOL.  (Some routers do.  Mine does)

I wake up a remote computer in exactly this way, and the remote computer is connected wirelessly via ethernet bridge to my main router.

You cannot use the built-in wireless card on the laptop to wake it up - because it is powered down when the laptop is powered down.

---

### Post by tomaasj on 2014-09-03
Hallo Weatherman2,

I will have to dive in all the aspects you describe and do some reading.

Thanks for the info since I am able to move on.

:)

---

