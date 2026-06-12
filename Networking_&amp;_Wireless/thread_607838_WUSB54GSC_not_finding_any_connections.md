---
title: "WUSB54GSC not finding any connections"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Cporzl23 on 2007-11-09
Hey, I believe I am really close to getting this to work, but I need one little bit of help. 

So I have my WUSB54GSC wireless card installed, "ndiswrapper -l" returns

"wusb54GSC : driver installed
                  device (13B1:0026) present"

The only problem is I start up the networking tool ( system -> admin ->  network) and there is no wireless connection. Any help would be wonderful.

---

### Post by invanitas on 2007-11-09
Try doing ```
iwlist scan
```

Can you manually enter the SSID of the network and get a connection?


I'm actually having a similar problem.  I have a linksys wmp54gs (broadcom, airforce one)  pci card that was working in x64 fiesty but now can't find networks in x64 gutsy.  I've tried all the x64 drivers for broadcom I can find in the forums, but the only ones that will get the link light to come on and will let ndiswrapper say the device is present are the ones I'm using now.  (They are also the ones I used in Fiesty.) iwilst scan gives no results and when I manually configure Network manager with my SSID (unencrypted) I get a 'connected' icon with 0 bars and 0% signal strength.

---

### Post by Cporzl23 on 2007-11-09
> **invanitas said:**
> Try doing ```
iwlist scan
```

Can you manually enter the SSID of the network and get a connection?


I'm actually having a similar problem.  I have a linksys wmp54gs (broadcom, airforce one)  pci card that was working in x64 fiesty but now can't find networks in x64 gutsy.  I've tried all the x64 drivers for broadcom I can find in the forums, but the only ones that will get the link light to come on and will let ndiswrapper say the device is present are the ones I'm using now.  (They are also the ones I used in Fiesty.) iwilst scan gives no results and when I manually configure Network manager with my SSID (unencrypted) I get a 'connected' icon with 0 bars and 0% signal strength.

I tried iwlist scan, it said something like ```
 This interface does not support this scan
```

I forgot to elaborate as usual, I am running Ubuntu 7.04 Fiesty, i386, on a pc with a wireless usb adapter. I installed the drivers via ndiswrapper.

I'm also not so sure on how to find the SSID of the network, but i'd assume that since the network tool isn't finding any wireless connection, then I'd doubt it.

---

### Post by Cporzl23 on 2007-11-09
Bump =/

---

### Post by Cporzl23 on 2007-11-10
> **Cporzl23 said:**
> Bump =/


=|

---

