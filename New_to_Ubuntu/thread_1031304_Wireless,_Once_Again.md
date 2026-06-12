---
title: "Wireless, Once Again"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mwfanelli on 2009-01-05
OK, I've installed Ubuntu 8.10 32-bit to try it out. My last attempt was 8.04 which came so tantalizingly close. But again, wireless is a problem.

I have a Dell 1501. The built in wireless card is a Dell Wireless 1490 Dual Band WLAN Mini-card. I know this card doesn't work with Ubuntu. I also have a Belkin Wireless G USB Network Adapter Model F5D7050. This worked fine, most of the time, with 8.04 a while back.

However, with 8.10, the Belkin sees the wireless networks (all unsecured), I choose one (any one),the little icon in the top bar spins, but I then get a disconnect notice. That's it. I need wireless to function!

Thanks for any help you can give me. Oh yeah, I'm running on Vista to get to the internet, so I know the wireless systems are working fine!

---

### Post by oilchangeguy on 2009-01-05
i'm running kubuntu 8.10 and using a linksys usb wireless adapter (desktop computer). and it works out of the box. i've tried other distros, and as you say the icon would spin but never connect. then i found that with dsl, sometimes you'll need to manually input things like the isp's ip addres, etc. if you've got dsl, get out your paper work, find the info, or contact your isp for the info.

---

### Post by mwfanelli on 2009-01-05
Thanks. But this is not DSL, its multiple-T1 lines at the local college. Finding an old-style land line Ethernet port is difficult!

---

### Post by superprash2003 on 2009-01-05
your wifi card should work with ubuntu.. the built in one i mean.. if im not mistaken it should be a broadcom.. try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by mwfanelli on 2009-01-05
I tried the Hardware Drivers solution using a cable and an ethernet port. Firefox worked well so I know teh connection is live. Unfortunately, after hitting "Activation", the "Downloading and Installing" box sat there for at leats 30 minutes and then stopped: nothing installed or activated. No message of any kind.

I then tried to do the updates listed in the icon. That spins for a while and then dies with some sort of locked file errors.

I will try to reload the Synaptic stuff and see if the Broadcom driver is there and whether it downloads or not. Sigh...

---

### Post by mwfanelli on 2009-01-05
Wow, just found out a few things:

1. The Update Manager fails all the time (the notification on the top bar), and worse, locks up files that prevents any other update app (such as Synaptic) to download or install. Restart required.

2. The Hardware Drivers app does exactly the same thing: spins it wheels, dies, and leaves files locked. Restart required.

3. Synaptic works well and downloaded/installed all 216 updates (hmmm). Now, my USB external wireless works but the internal Dell one is still dead (can't download the driver, #2 above).

So... I have wireless (the external unit is fine). Thanks for all the help! Great forum.

The second and last drop-dead hurdle is to try and get Microsoft Office to work. For the stuff I do, nothing else out there is a reasonable substitute. Believe me, I've tried! Wine has been downloaded via Synaptic, here I go...

---

