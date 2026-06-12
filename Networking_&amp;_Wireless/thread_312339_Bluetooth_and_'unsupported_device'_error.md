---
title: "Bluetooth and 'unsupported device' error"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by camilluk on 2006-12-04
Hi all,
 
I have successfully installed (at least I think I have) the bluez-utils on my kubuntu 6.10 pc and now I'm trying to use the mobile to connect to the internet via gprs/edge/umts. Btw, this works fine if I use the USB cable instead of bluetooth.
 
If I do an 'hcitool scan' I can see the MAC address and my phone's name. If I check which channel it's using, I can see it is using channel 3 and the channel is clean.
 
When I start the pairing procedure from the phone I get a pop-up message from KDE-Bluetooth and enter the passkey requested by the phone.
 
So far no problem, or at least I don't see any unexpected errors or behaviours, but then the two (PC and mobile phone) are not connected. My phone is not listed among the paired devices in KDE-Bluetooth (and frankly I can't figure out how to search for it from the PC).
 
Basically, the phone can 'see' the pc, it apparently pairs with it, as the pc is listed on the paired devices list of the phone, but if I try to connect to the detected device (my PC), the phone tells me that the device is unsupported.
 
As for my ppp connection, obviously the modem isn't detected by the pc, so I'm not able to configure properly KPPP, but I don't think that's where the problem is. I don't see how I can try to exchange files between the two either, so I suppose it all comes down to the two devices talking to each other and once that happens I think the modem and the connection will work fine.
 
Any ideas?

Edited:
It's a workaround more than a proper solution, anyway... it all works if I initiate a connection from the terminal with the command:
```
cat /dev/rfcomm0
```

---

