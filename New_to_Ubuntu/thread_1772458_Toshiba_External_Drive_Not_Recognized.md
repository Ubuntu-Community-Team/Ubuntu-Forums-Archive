---
title: "Toshiba External Drive Not Recognized"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by maclovio78 on 2011-05-31
I was trying to get some files from my Toshiba 250GB External drive. When I plugged it to the usb port the light on the drive turned on, but it never got recognized by my system. I was able to use a Sandisk Cruzer, but would like to be able to use this Toshiba.

---

### Post by Toz on 2011-05-31
Plug it in again then open a terminal window, and type in```
dmesg
``` and post back the last 20 lines or so.

---

### Post by maclovio78 on 2011-06-02
here is what it posts.


[ 3638.540806] usb 1-6.4: new high speed USB device using ehci_hcd and address 2
[ 3639.073499] usb 1-6.4: USB disconnect, address 2
[ 3640.080324] usb 1-6.4: new high speed USB device using ehci_hcd and address 6
[ 3640.609274] usb 1-6.4: USB disconnect, address 6
[ 3641.610381] usb 1-6.4: new high speed USB device using ehci_hcd and address 7
[ 3642.145325] usb 1-6.4: USB disconnect, address 7
[ 3643.150284] usb 1-6.4: new high speed USB device using ehci_hcd and address 8
[ 3643.425124] usb 1-6.4: USB disconnect, address 8
[ 3644.680339] usb 1-6.4: new high speed USB device using ehci_hcd and address 9
[ 3644.961181] usb 1-6.4: USB disconnect, address 9
[ 3645.960416] usb 1-6.4: new high speed USB device using ehci_hcd and address 10
[ 3646.496962] usb 1-6.4: USB disconnect, address 10
[ 3647.500289] usb 1-6.4: new high speed USB device using ehci_hcd and address 11
[ 3648.033012] usb 1-6.4: USB disconnect, address 11
[ 3649.041339] usb 1-6.4: new high speed USB device using ehci_hcd and address 12
[ 3649.568921] usb 1-6.4: USB disconnect, address 12
[ 3650.570418] usb 1-6.4: new high speed USB device using ehci_hcd and address 13
[ 3651.104841] usb 1-6.4: USB disconnect, address 13
[ 3652.110296] usb 1-6.4: new high speed USB device using ehci_hcd and address 14
[ 3652.641385] usb 1-6.4: USB disconnect, address 14
[ 3653.640840] usb 1-6.4: new high speed USB device using ehci_hcd and address 15
[ 3654.176666] usb 1-6.4: USB disconnect, address 15
[ 3654.920270] usb 1-6.4: new high speed USB device using ehci_hcd and address 16
[ 3655.456477] usb 1-6.4: USB disconnect, address 16
[ 3656.461685] usb 1-6.4: new high speed USB device using ehci_hcd and address 17
[ 3656.992390] usb 1-6.4: USB disconnect, address 17
[ 3658.000359] usb 1-6.4: new high speed USB device using ehci_hcd and address 18
[ 3658.528443] usb 1-6.4: USB disconnect, address 18
[ 3659.530430] usb 1-6.4: new high speed USB device using ehci_hcd and address 19
[ 3660.064360] usb 1-6.4: USB disconnect, address 19

---

### Post by Toz on 2011-06-02
It might be a hardware problem. 
- Is this a known good drive? 
- Does it work on another computer? 
- Do you have another cable you could try? 
- How is the drive plugged in? Is it going directly to the computer or is it going through some sort of hub?

With the drive plugged in, open a terminal window and type in the following and post back the results:```
uname -a
lsusb
lsmod
```

Have you tried unplugging the drive and then plugging it back in? If so, do you get the same error message? This time, after you plug it in, can you run:```
dmesg | grep "usb 1-6.4"
```and post back the results.

---

### Post by maclovio78 on 2011-06-02
I think I solved it. I had it connected to a 4-port usb hub. I reconnect it directly and it worked. Thanks.

---

### Post by jtarin on 2011-06-02
Mark this post as solved then please.

---

### Post by wildmanne39 on 2012-08-11
Old thread closed.

---

