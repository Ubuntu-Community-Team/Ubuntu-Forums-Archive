---
title: "wn220 (Prism 2) USB wireless device does not like me anymore"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by supremedalek on 2008-05-14
I have here a wn220 (a.k.a. WRUB-2011i, by Ashton Digital), which is a Prism 2 device. Before, to get it running in my ubuntu 7.10 laptop, I would use linux-wlan-ng, which I installed using synaptic:

```
raub@monaco:~/todo$ wlanctl-ng version
wlanctl-ng: 0.2.9
raub@monaco:~/todo$ 
```

```
raub@monaco:~$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
message=lnxreq_ifstate
  ifstate=enable
  resultcode=success
raub@monaco:~$ 
```

But, after doing a few updates using the update manager, it now acts like it does not know about this device anymore:

```
raub@monaco:~$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable 
wlanctl-ng: No such device
raub@monaco:~$
```

Any reason it could be ignoring me like that?  Here are the relevant dmesg lines:

```
[  281.924000] usbcore: registered new interface driver prism2_usb
[ 1820.208000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 1820.332000] usb 2-1: device descriptor read/64, error -71
[ 1820.560000] usb 2-1: device descriptor read/64, error -71
[ 1820.776000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[ 1820.896000] usb 2-1: device descriptor read/64, error -71
[ 1821.120000] usb 2-1: device descriptor read/64, error -71
[ 1821.336000] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 1821.744000] usb 2-1: device not accepting address 8, error -71
[ 1821.856000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[ 1822.264000] usb 2-1: device not accepting address 9, error -71

```

To me it sounds like the usb device and the laptop do not like each other anymore but so far my google-fu has not been very fruitful. Any suggestions? I will try it in my OSX laptop just to make sure it is still happy.

---

### Post by supremedalek on 2008-05-31
Resurrecting this old thread of mine, do I still need to deploy linux-wlan-ng to make a prism2 card to work under 8.04 or it should work out of the box?

---

### Post by supremedalek on 2008-06-03
Update: it seems one the wires that went from the USB connector to the board broke off because of the hinge design:
[IMG]http://kudria.com/projects/computer/etc/WN220_01.jpg[/IMG]
So, I found some old/broken USB device, cut its cable, and soldered it as a replacement to the old hinge thingie:
[IMG]http://kudria.com/projects/computer/etc/WN220_02.jpg[/IMG]
So, I tested it and it seems to work. Now it is just a matter of making it all fit on its original case and life will be good.

---

