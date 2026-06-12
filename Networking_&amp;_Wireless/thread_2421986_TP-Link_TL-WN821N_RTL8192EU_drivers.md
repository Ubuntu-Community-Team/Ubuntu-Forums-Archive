---
title: "TP-Link TL-WN821N RTL8192EU drivers"
date: 2019-06-30
forum: Networking &amp; Wireless
---

### Post by J.Erik.C on 2019-06-30
**Bus 005 Device 004: ID 2357:0107 TP-Link TL-WN821N Version 5 RTL8192EU**

It works but the signal is very weak, -80 -90 signal.
The USBcard on the box shows it should be Version6 not Version5 as seen from the lsusb above.

Is there something I can do to update this driver or make it work properly?
I am running on 19.04

Cheers,

---

### Post by wildmanne39 on 2019-06-30
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by J.Erik.C on 2019-06-30
That's fair enough. Sorry :)

---

### Post by wildmanne39 on 2019-06-30
No worries, I moved it here because you are more likely to get the help you need in this syb-forum.

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help.

---

### Post by jeremy31 on 2019-06-30
There is not a fix for the 5.0 kernel that I know of, if you want to use Ubuntu 18.04 with the 4.15 kernel then [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver) should work

---

### Post by J.Erik.C on 2019-06-30
Here is the output.
I hope I did this right.

[http://paste.ubuntu.com/p/fz4SvwSc4f/](http://paste.ubuntu.com/p/fz4SvwSc4f/)

---

### Post by J.Erik.C on 2019-07-01
Any help? 

So if I understood right, the best for kern5.0 is my actual situation, meaning:
- low signal (-50 -60 with access point few steps away)
- the driver TL-WN821N Version 5 RTL8192EU , not version 6 which is written on the box of the card.

Stupid noob question but I have to do it to be 100% sure: 
There is noway to use a 4.15 driver on a 5.0 kernel right?

---

### Post by jeremy31 on 2019-07-01
I found a source that claims to support the 5.0 kernels
```
sudo apt install git build-essential dkms
git clone https://github.com/clnhub/rtl8192eu-linux.git
sudo dkms add ./rtl8192eu-linux
sudo dkms install rtl8192eu/1.0
```


You can actually skip this next step and reboot as you installed Ubuntu in Legacy boot instead of UEFI
Check ```
mokutil --sb-state
``` as Secure Boot will need to be disabled

---

### Post by J.Erik.C on 2019-07-04
I am testing this!
It seems the signal improved and that it works ( before with low signal it was impossible to open  a webpage).
I will test it a little. 
Thank you so much for your help anyways!

---

### Post by J.Erik.C on 2019-07-04
Unfortunatelly airodump-ng wlan is still showing bad results.
I had a successfull connection to the router, disconnected after some minutes, not working anymore.
After putting in monitor mode, it's not connecting anymore.
Maybe I messed up something with this driver. I am not good enough to find out.

I think I will have to give up and find an adapter working properly.
But it's difficoult to understand what to buy.
Any suggestion?

---

