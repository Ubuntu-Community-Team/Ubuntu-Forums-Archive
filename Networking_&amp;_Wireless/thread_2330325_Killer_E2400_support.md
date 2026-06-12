---
title: "Killer E2400 support?"
date: 2016-07-10
forum: Networking &amp; Wireless
---

### Post by soft22dvd3 on 2016-07-10
Is the Killer E2400 supported in Ubuntu 16.04? I read that this was not supported last year so am wondering if 16.04 fixed that.

Should I stick with Intel and Realtek since they are more popular (and I assume have better support)?

---

### Post by jeremy31 on 2016-07-10
Yes it is.  I think that device is supported in the alx module
```
pci:v00001969d0000E0A1
```
Does ```
lspci -nnk | grep -iA2 net
``` show the Killer E2400 device as [1969:e0a1]

There were a couple workarounds for earlier versions of Ubuntu.  I even made a dkms package that worked for people

If you have issues, try setting the MTU to 8192 in Network Manager

---

