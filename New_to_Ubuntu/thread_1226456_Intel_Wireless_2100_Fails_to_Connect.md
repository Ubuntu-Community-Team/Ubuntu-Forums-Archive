---
title: "Intel Wireless 2100 Fails to Connect"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by regomodo on 2009-07-29
#

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
What kind of card do you have?

PCI:```
sudo lspci | grep network -i
```or USB:```
lsusb
```Post one of those output based on your card.

Also post the output of```

iwconfig
```

---

### Post by nhasian on 2009-07-29
i'll bet you have an Atheros or Broadcom wifi chipset and your using an older version ubuntu ](*,) try Ubuntu 9.04 or Karmic Alpha3

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
Are you sure it's not a firmware issue with your router?

:)

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
Hmmm, let me look at launchpad.....

what rev of the card do you have?

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
> **regomodo said:**
> 04
All I can say now is install the latest firmware for your card and extract the files into /lib/firmware

:) Hope that works :)

[http://ipw2100.sourceforge.net/firmware.php](http://ipw2100.sourceforge.net/firmware.php)

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
what about:
```
rmmod ipw2100
modprobe ipw2100
```

---

### Post by regomodo on 2009-07-29
#

---

### Post by LookTJ on 2009-07-29
> **regomodo said:**
> Just get the single green light and the spinning blue tail until it times out.
Might be a kernel issue.

I doubt it's the gnome's network manager.

:)

---

### Post by regomodo on 2009-07-30
#

---

