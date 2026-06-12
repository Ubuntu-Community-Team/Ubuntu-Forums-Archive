---
title: "PRO/Wireless 2200BG Wireless Problems"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by slolivin on 2008-05-09
Hi all.

I've been using Linux at work for a bit and a friend suggested I take a look at Ubuntu.  I've only been writing scripts and what not so the admin side is completely new to me.

Install went great, but I can't seem to get wireless working.  I go to Network Settings and I don't even see a wireless option in the list, just "Wired Connection" and "Point to point connection".  I swear wireless connection was there the last time I logged in, but I don't see it now....

If I do dmesg | grep ipw2200 i get the following:
ipw2200: Intel(R) PRO/Wireless 2200/915 Network Driver, 1.2.2kmprq
ipw2200: Copyright(c) 2003-2006 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Failed to send TX_POWER: Command timed out.
ipw2200: Unable to initialize device after 5 attempts.
ipw2200: failed to register network device
ipw2200: probe of 000:05:04.0 failed with error -5

The wireless works fine on the windows partition so I know i'm just missing something here.

One other small problem is shutting down the laptop from Ubuntu.  I go to shutdown, the screen comes up and all goes well.  Except when the laptop should power down the screen stays on.  Granted it's just a black screen, but I know it's not off because the lights are still on on the laptop.

I saw another thred that suggested the following:
Add apm power_off=1 to /etc/modules 

I did that but still no luck.  The only way to shutdown is to hold the power button for a few seconds.

Any help would be appreciated.

---

### Post by slolivin on 2008-05-13
Disregard this post.  I've done some research and it looks like lots of people are having trouble wih Wireless on this version of Ubuntu.  I have uninstalled and will wait for a new version with these issues addressed to be released :(

---

