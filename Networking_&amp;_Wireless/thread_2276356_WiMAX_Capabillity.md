---
title: "WiMAX Capabillity?"
date: 2015-05-01
forum: Networking &amp; Wireless
---

### Post by crafterguy1701 on 2015-05-01
I had always seen "wmx0" on my network stack and thought nothing of it.  I looked up what it was the other day, and i found its something called WiMAX.  In the network manager the Mobile Broadband option is grayed out (not sure if WiMAX is classified as that?) 

when running the command ```
rfkill list
``` i get the output: 

```
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: i2400m-usb:2-1.6:1.0: WiMAX
        Soft blocked: yes
        Hard blocked: no
11: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```

The output of ```
lspci
``` gives this for my wireless card:

```
Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
```

I looked up this wireless card on the Intel site and according to them this card doesnt have WiMAX capabillity.


What is going on here?

---

