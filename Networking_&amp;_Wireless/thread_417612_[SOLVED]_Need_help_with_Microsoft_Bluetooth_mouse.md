---
title: "[SOLVED] Need help with Microsoft Bluetooth mouse"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by PastorTaz on 2007-04-21
I'm new to Linux and can't seem to get my bluetooth mouse working on a constant basis.  I've read quite a few posts on how to get it to work and sometimes I can then the next time I use my mouse it won't work.  

I have a Dell Latitude 820 with internal Dell Bluetooth.  My mouse is a Microsoft wireless 8000.

I've tried to edit the /etc/default/bluetooth file and here is what I have now
```
    HIDD_ENABLED=1
    HIDD_OPTIONS="-i 00:12:5a:64:35:ce --server"
```

I try the "sudo hidd --server" and this is what I get
```
    Can't listen on HID control channel: Address already in use
```

Is there anything I'm missing?

Thanks,

---

### Post by PastorTaz on 2007-04-21
Don't know why, but it is working now.  When I posted it was not and I did nothing to make it work.

---

