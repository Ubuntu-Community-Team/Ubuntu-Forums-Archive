---
title: "linux-wlan-ng and pcmciautils"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by Gris on 2006-07-19
Hi Everyone

New user of Linux here so please excuse if this has a well known solution. :) 

I have a DWL-120d (USB version) which I have to use to connect to the Internet. It works great on Windows XP. I have installed Ubuntu 6.06 and it does not recognise the card. I burnt to a CD:

[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.3-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.3-1ubuntu7_i386.deb)

and tried to "sudo dpkg -i" it. I get the error message:

* linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs

And now I'm stuck. I tried "dmesg | grep prism" and got:

prism2usb_init: prims2_usb.o: 0.2.2 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
prism2sta_ifstate: hfa384x_drvr_start() failed, result=-5

Can anyone help me please?

David

---

### Post by tormod on 2006-08-29
> **Gris said:**
> I get the error message:

* linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs

And now I'm stuck. I tried "dmesg | grep prism" and got:

prism2usb_init: prims2_usb.o: 0.2.2 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
prism2sta_ifstate: hfa384x_drvr_start() failed, result=-5

Can anyone help me please?

David

The pcmciautils message is nothing to worry about.

Can you try unplugging and plugging back your USB card a couple of times to see if you can avoid the hfa384x_drvr_start() message?

---

