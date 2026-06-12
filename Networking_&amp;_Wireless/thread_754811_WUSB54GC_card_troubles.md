---
title: "WUSB54GC card troubles"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by evanct on 2008-04-14
this is ubuntu 7.04

so i followed the instructions at [http://ubuntuforums.org/showthread.php?t=414006](http://ubuntuforums.org/showthread.php?t=414006). everything seemed to go smoothly, when i run ndiswrapper -l i get:

```
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)

```

and the card itself is blinking constantly. when i got to the Wireless assistant, it shows one ESSID: MGM108(wtf is that?), instead of wlan0 or something. anyway, here are the settings i used:

IP: 192.168.1.125
Broadcast: 
Netmask: 255.255.255.0
Gateway: 192.168.1.1
Domain: 
Primary DNS: 194.168.4.100
Secondary DNS: 194.168.8.100

and then it says a WEP key is required. i have no idea what my WEP key is nor how to find out. so naturally it isn't able to connect.

the thing is, this same card with the same driver was working fine about a month ago. then i used ethernet for a while, but now because of certain circumenstances i'm forced to use wireless again i've changed nothing since the last time i used it, yet now it doesn't work.

can anyone help?

---

### Post by sofasurfer on 2008-04-21
I'm a complete failure at getting my WUSB54GC going but I do have an answer for you.
A WEP key is the security code that you chose when you installed and set up your router. If your network adapter does not have the same code entered then it will not be able to communicate with your router.

Find your routers I.P. address by reading this:
[http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm](http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm)

My Belkin router uses 192.168.2.1.
Enter the number into your address bar and you will find all kinds of data and confige options on your router, including security stuff.

Anyway, this is what this nooby thinks. Hope it works.
If it help, repay me by visiting my thread and solving my crisis. 
Thanks.

---

