---
title: "How to find out what network card I am using?"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by NakedGreekStatue on 2005-08-09
My laptop's internet currently doesn't work because the installer didn't detect my network card. How do I find out what network card I am using so I can get a driver?

The laptop normally connects to the internet via a connection to a 2Wire HomePortal DSL connection over the home phoneline. The laptop connects to the phoneline via a USB adapter. Any help?

---

### Post by PeP on 2005-08-09
[QUOTE=NakedGreekStatue]My laptop's internet currently doesn't work because the installer didn't detect my network card. How do I find out what network card I am using so I can get a driver?

The laptop normally connects to the internet via a connection to a 2Wire HomePortal DSL connection over the home phoneline. The laptop connects to the phoneline via a USB adapter. Any help?[/QUOTE]
then you have no network card, just a usb modem.
lsusb will tell you more about it
in a terminal type:
lsusb
with the usb device plugged in :-)

---

### Post by NakedGreekStatue on 2005-08-09
Thnx. From the the lsusb command I got:

```

Bus 001 Device 002: ID 1630:0011
Bus 001 Device 001: ID 0000:0000

```

I really have no idea how to use this information though. :|

---

### Post by PeP on 2005-08-09
[QUOTE=NakedGreekStatue]Thnx. From the the lsusb command I got:

```

Bus 001 Device 002: ID 1630:0011
Bus 001 Device 001: ID 0000:0000

```

I really have no idea how to use this information though. :|[/QUOTE]
1630:0011
it is a 2Wire USB converter (thanks google ;-)

---

### Post by NakedGreekStatue on 2005-08-10
Cool, that solves that, but I still don't know how to get the internet working. That posting on the redhat mailing list didn't offer much help and I really need to get this working. Help?

---

### Post by NakedGreekStatue on 2005-08-10
I did find drivers for the device for WIndows and MacOSX but no linux.  :?
[http://www.2wire.com/?p=266](http://www.2wire.com/?p=266)

---

