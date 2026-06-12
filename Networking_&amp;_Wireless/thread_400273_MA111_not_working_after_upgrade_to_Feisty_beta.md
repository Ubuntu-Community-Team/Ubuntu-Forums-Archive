---
title: "MA111 not working after upgrade to Feisty beta"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by JasonRivers on 2007-04-03
Hi all

I had my MA111 (Prism2_usb) working fine in 6.10 I upgraded to 7.04 and its now not working.

If i do "iwconfig"

I get 

wlan0            no wireless extensions


I tried:

```
modprobe -r prism2_usb

modprobe -r ndiswrapper

modprobe ndiswrapper
```

then reconnected my MA111 and the network Icon near the clock came up with the wireless signal strength for a split second, then went away again.

if anyone can help please let me know

Jay

---

### Post by JasonRivers on 2007-04-21
*bump*

---

### Post by dangermouse28 on 2007-05-03
Hi,

My MA111 works like a charm. This is what I did:

Fresh install (sorry - it's the best way)

Insert MA111 and do dmesg to check it's found.

Leaving the adaptor plugged in, install linux-wlan-ng from the CD.

Unplug the adaptor and reboot.

Plug in your adaptor and go to Admin - Networks, you should see wlan0 listed in Roaming mode.

Go into the Properties, uncheck Roaming mode and insert your details.

Close, remove adaptor and reboot again.

Insert adaptor and you're in business!

You might not need so many reboots but they worked for me - good luck!

---

### Post by JasonRivers on 2007-05-03
no, this did not work for me, it still comes up as "Wired Connection" :( but its alias is "Wlan0"

---

### Post by dangermouse28 on 2007-05-10
Check to see which version of the MA111 you have

[www.kbserver.netgear.com/products/ma111.asp]("www.kbserver.netgear.com/products/ma111.asp")

should help.

The method I described has worked on 6 different laptops and desktops, but is is for version v1.

---

### Post by JasonRivers on 2007-05-10
yes I have Version 1 of the adapter, the adapter works fine in Edgy, but in Feisty, when I plug it in and then do IWCONFIG it shows the wireless infoe, then 5 seconds later I do IWCONFIG and it says "No wireless extentions"

Jason

---

