---
title: "Aspire 5000 &amp; Wireless Switch"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by reboskyz24 on 2009-06-07
I just installed Jaunty 9.04 on an Acer Aspire 5000 notebook and cannot get the wireless working.  I've been through the guides and other forum posts to no avail.

I think the problem stems from the hardware switch being a toggle switch, and no matter how many times I press it, the light never comes on.

I've installed the Windows wireless driver using ndiswrapper.  When I access Windows Drivers under System --> Administration, I get an error when it opens saying "Unable to see if hardware is present."  When I press okay, I can see the driver is installed (bcmwl5) and now it says hardware is present.

Any help would be greatly appreciated as I'm hesitant to go back to Windows, but wireless connectivity is paramount.

---

### Post by keplerspeed on 2009-06-07
Ok what exactly is the wireless card? To find out enter this and the make/model will be in there somewhere:
```

lspci

```

Also try going to system>admin>hardware drivers. Maybe your card is supported. If a driver is there for the wireless card, install it.

---

### Post by reboskyz24 on 2009-06-07
Broadcomm BCM4318

No proprietary drivers are in use on this system.

---

