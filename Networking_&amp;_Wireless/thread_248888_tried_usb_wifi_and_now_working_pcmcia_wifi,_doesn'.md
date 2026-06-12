---
title: "tried usb wifi and now working pcmcia wifi, doesn't"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by chrluc on 2006-09-01
hello all, 

I came across a usb wifi device and decided to try it, so I plugged it in and and it was recognized by the networking gui, so I tried to configure it... and it froze the system. I restarted, and unplugged it and tried to use the pcmcia card that has always worked and it links and shows I'm connected to the router but when I access the Internet it cannot connect... still have wired connectivity but no wireless... any ideas on how to fix it? could I just delete and reinstall the drivers?   

thanks

---

### Post by chrluc on 2006-09-03
bump

---

### Post by NetworkGuy on 2006-09-03
We will need more information.

What is the brand/model of the wifi device you want to use.

With it plugged in, can you post the results of the following commands?

If pcmcia type
```
lspci
```

If usb type
```
lsusb
```

And then type these regardless
```
iwconfig
```
```
ifconfig
```

T

---

