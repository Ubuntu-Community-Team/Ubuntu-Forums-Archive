---
title: "ndiswrapper issue"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by GhostToast on 2008-11-07
Hi all,

I just installed Ubuntu 8.10, and I got my driver (dellnic) installed through ndiswrapper. I can view my wireless networks, but I cannot connect to the internet.  I have a Dell 1450 USB adapter.  I installed the packages ndiswrapper-common, ndiswrapper-utils, and ndisgtk.  On my 1450 USB adapter, there is supposed to be 2 lights, one is supposed to be solid, (that one is on) and another one is supposed to be blinkng (that one is not on).  

Can someone please help me?

Thanks. :)

---

### Post by dmizer on 2008-11-07
Please post the output of the following

```
lshw °C network
```
```
ndiswrapper °l
```

---

### Post by Ayuthia on 2008-11-07
> **dmizer said:**
> Please post the output of the following

```
lshw °C network
```
```
ndiswrapper °l
```

I think that dmizer meant:
```
lshw -C network
ndiswrapper -l
```

---

