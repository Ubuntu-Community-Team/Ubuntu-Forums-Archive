---
title: "Belkin USB G Wireless"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by A.I. BOT on 2007-12-25
I got the Belkin USB G Wireless Adapter as a gift. Plugged it in, put the install cd in and ran:

> 
# ndiswrapper -i rt73.inf
# modprobe ndiswrapper
# ndiswrapper -l
rt73 : driver installed
        device (050D:705A) present (alternate driver: rt73usb)
# ndiswrapper -m


Everything seems to have been done and installed fine. So in the network manager, my wireless network was detected and showed up. I clicked it, it asked for my passphrase, I put it in and it trys to connect but it wont. I know my passphrase is correct, so it a ndiswrapper or driver issue or something?

Thanks.

---

### Post by Stranger255 on 2007-12-25
I have the same problem although i didnt have to install any drivers from the nswrapper, however im using a wireless belkin card, the card flashes and confirms it is both sending and receiving but i cannot get on the internet and i cannot even connect to my router 

Sorry if im replying in the wrong area, totally new to the forums and to ubuntu

---

### Post by A.I. BOT on 2007-12-26
Dont know how I managed to get it to work ...

I went into my router's config, reset the wireless, set it to a "WEP 128-bit Passphrase", set the passphrase and clicked finished. My router rebooted. Then, I installed rt2500 and rt2500-source from the repos and then rebooted my system.

Once that was done, I clicked my wirless network via the network manager applet in the gnome panel. Put in my passphrase and it connected perfectly. :)

Thanks. Dunno if thats any help to any one though.

---

