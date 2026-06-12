---
title: "wireless usb adapter doesn't work"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Shiroku on 2006-11-01
my wireless usb adapter (Sitecom WL-113 v1 002) doesn't work...
the model 'sitecom wl-113' work succefull, but the new model 'sitecom wl-113 **v1 002**' doesn't work...
(my OS: Kubuntu 6.10)


Some screenshot:
when i run ifconfig:
[IMG]http://www.nonsologuide.altervista.org/_altervista_ht/ifconfig.png[/IMG]

what is wmaster???


when i run iwconfig ('FRC' is my wireless network name):
[IMG]http://www.nonsologuide.altervista.org/_altervista_ht/iwconfig.png[/IMG]

when i run dhclient:
[IMG]http://www.nonsologuide.altervista.org/_altervista_ht/dhclient.png[/IMG]

'wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801' 
??? but what is wmaster??


when i run the wireless assistant (with Wireless Assistant i can find my wireless network, but...):
[IMG]http://www.nonsologuide.altervista.org/_altervista_ht/wassistant_wlan.png[/IMG]
[IMG]http://www.nonsologuide.altervista.org/_altervista_ht/wassistant_wmaster.png[/IMG]

---

### Post by Shiroku on 2006-11-05
no ideas?

---

### Post by Shiroku on 2006-11-07
if i run dmesg, this is the output:

when i start kubuntu and plug in my usb wireless adapter, if i run dmesg, this lines are added:
[17179713.512000] usb 2-2: new high speed USB device using ehci_hcd and address 2
[17179713.780000] usb 2-2: configuration #1 chosen from 1 choice
[17179714.412000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179714.532000] wmaster0: Selected rate control algorithm 'simple'
[17179714.628000] usbcore: registered new driver rt73usb

then if i run 'sudo ifconfig wlan0 up', if i run dmesg, this line is added:
[17179725.764000] wlan0: no IPv6 routers present

if i scan with wireless assistant, if i run dmesg, this lines are added:
[17179952.640000] wlan0: starting scan
[17179953.588000] wlan0: scan completed

---

### Post by Shiroku on 2006-11-13
if i run:
```

sudo iwconfig wlan0 mode managed essid 'FRC'

```
(FRC is my network name)

the output is:
**    SET failed on device wlan0 ; Device or resource busy.**

---

