---
title: "[SOLVED] Wireless Express Card"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by KentS on 2007-11-07
I'm trying to set up Merlin XU870 on a machine running Dapper Drake, kernel version 2.6.15-27-386. I'm using this guide:
[http://www.novatelwireless.com/support/merlin-xu870-linux.html](http://www.novatelwireless.com/support/merlin-xu870-linux.html)

2 Problems:
1. The guide assumes that I have already successfully installed the XU870 Linux drivers.
But I don't manage to find any drivers. Is the script package mentioned in step 5 the driver?

2. My output from
```
sudo tail –f /var/log/messages
``` 
after inserting the card is
```
Nov  7 23:11:51 kent-laptop kernel: [17181713.784000] ohci_hcd 0000:00:0b.0: wakeup
Nov  7 23:11:51 kent-laptop kernel: [17181714.168000] usb 2-2: new full speed USB device using ohci_hcd and address 2

```

Now, for step 3 I need the device the card was attached to, but this doesn't show up in the above posted output.

I would really appreciate help with this. This is the last thing remaining before I'm free from Windows.

---

### Post by KentS on 2007-11-07
Never mind. Wrong kernel version...

---

