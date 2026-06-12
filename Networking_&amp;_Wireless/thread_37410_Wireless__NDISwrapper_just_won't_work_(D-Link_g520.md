---
title: "Wireless / NDISwrapper just won't work (D-Link g520+ / ACX111)"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2005-05-27
I tried, read the HOWTO's, tried some more, posted a question and got the answer that someone had this WiFi-card working out of the box... But not so for me. 

I installed Ubuntu and got NDISwrapper right away. Tried the HOWTO in these forums, but NDISwrappper just acted really strange:

NDISwrapper -i driver.inf said the driverfile is not valid. 
NDISwrapper -l shows the file anyway.
NDISwrapper -e will not remove it, since it says it has no driver installed. 

Right about that time I got the post from KiwiNZ that he had the card working out of the box. *slaps forehead* Didn't even bother to try if Ubuntu saw the card, how stupid of me.

So back to the GUI, Network settings -> It showed my wlan0 card. It even listed my Wireless AP in the SSID list! Fed my DNS servers in the settings, and fired up Firefox. But no go, it won't see any website.

Tried to ping my router, but there's "no network connection".

So now I'm left with 2 different programs (native Ubuntu driver / NDISwrapper) both halfway there, but none works completely.

Any suggestions? Maybe uninstall NDISwrapper as it might be in the way of the native driver? Or the other way around: remove native driver so NDISwrapper will work properly? I'm all out of ideas.

Thanks in advance for any suggestions!

---

