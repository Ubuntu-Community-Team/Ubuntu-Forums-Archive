---
title: "Installed a new wireless card - is it detected?"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Rovdjur on 2007-08-23
Well I bought a new internal wireless card for my laptop, and I do not know how to get it working.

lspci returns this:
```
03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
```

I am assuming the Unknown Device means it just can not detect the card fully?

I already tried installing the madwifi drivers, and they do not work at all.

iwconfig returns this:

```
jonas@tux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

```

Any ideas? Thanks.

---

### Post by kevdog on 2007-08-23
Try posting 
lshw -C network 

Id be curious about the output.

---

