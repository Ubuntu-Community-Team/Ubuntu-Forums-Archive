---
title: "Can't Connect to Internet"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by J2Long on 2009-08-30
I just installed Xubuntu and am using it through Dual Boot, I used UNetBootin to install it.  I can connect to the internet on XP via my USB wireless adapter, but can not do so on Xubuntu and I really am lost on how to go about fixing it.  The product I'm using to get wireless is from Qwest, called USB Wireless N Network Adapter. I hope I included all pertinent information, this is my first rodeo with Linux.

---

### Post by cariboo on 2009-08-30
Welcome.

We need to know what chipset your wireless device has. Could you open an Applications-->Accessories-->Terminal and type:

```
lsusb > lsusb.txt
```

The above command list your usb devices and pipes it to a text file, in this case lsusb.txt, you can copy the text file to your Windows partition and paste it in your next message.

---

