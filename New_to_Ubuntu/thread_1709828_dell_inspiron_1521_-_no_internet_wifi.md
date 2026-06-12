---
title: "dell inspiron 1521 - no internet wifi"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by silent1643 on 2011-03-18
just installed the latest version of ubuntu on my dell inspiron 1521 and cannot get my wifi connection to work - i even tried a straight Ethernet connection and also failed..

i have tried following this guide
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and did add the ubuntu install cd as a source under ubuntu software center - and i did find the broadcom kernel to install however - once i click install

i get error saying failed to download the package files - file not found?? this should be coming off the cd so nothing should be "downloaded"

thoughts?

---

### Post by wep940 on 2011-03-19
First off, are you sure it's a Broadcom card?  If so, what model/chipset (hint:  lspci).

---

### Post by isparkes on 2011-03-19
> **wep940 said:**
> First off, are you sure it's a Broadcom card?  If so, what model/chipset (hint:  lspci).

Please show us the output to this from the terminal:

```
sudo lshw -C network
```

---

