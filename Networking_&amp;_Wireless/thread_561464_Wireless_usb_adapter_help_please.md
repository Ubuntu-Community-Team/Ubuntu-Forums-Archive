---
title: "Wireless usb adapter help please"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by fozy420 on 2007-09-27
Ok well, if i go into the network options it has found my wireless network but i haven't installed any drivers? Does this mean that I still have to install drivers or could i connect to it ? If i need to install how would I go about installing drivers for my Belkin Wireless G Usb adapter ?
Sorry for the noobness :(

---

### Post by graywizard on 2007-09-27
i am new too - but if it finds the signal then it means that something is working.

---

### Post by wirelessmonkey on 2007-09-27
Some/Many wireless adapters are supported in the Linux kernel.  Occasionallly you will have to work some special voodoo to get WPA working though.

Best of Luck

---

### Post by fozy420 on 2007-09-27
ok i tried loading firefox and it didn't work :( I don't know what to do tbh, how do you even connect!

---

### Post by teaker1s on 2007-09-27
open up terminal and type ```
lsusb
``` this will give chipset and then you can go from there,some are natively supported,some need driver and some use ndiswrapper with windows driver

---

### Post by fozy420 on 2007-09-28
ok i think i installed the driver 

```

blkwgu : driver installed
        device (050D:705C) present (alternate driver: zd1211rw)

``` 

and I get this when i type a command i forget which :p

```

eth1      IEEE 802.11b/g  ESSID:"MYNETWORK"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <my mac>  
          Bit Rate=11 Mb/s   
          Link Quality=67/100  Signal level=43/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

How do I connect? I tried going to windows wireless drivers but it doesn't open, firefox and open office also will not open :/

---

### Post by wirelessmonkey on 2007-09-28
It looks to me like you are associated to the Network.  Try: sudo dhclient eth1

---

### Post by fozy420 on 2007-09-28
lol, i reinstalled ubuntu with my card plugged in and it worked straight away! :) thanks for the help.

---

