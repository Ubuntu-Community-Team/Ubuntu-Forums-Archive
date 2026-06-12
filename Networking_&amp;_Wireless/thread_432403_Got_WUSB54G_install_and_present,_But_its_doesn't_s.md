---
title: "Got WUSB54G install and present, But its doesn't show pu in network."
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Kanti on 2007-05-04
I just got my WUSB54G driver install and when i do NDISWRAPPER-L its said:("Driver install and present") with code xxxx. I try ndiswrapper -m but still don't show up. any I dea?

---

### Post by Floppyjoe on 2007-05-04
> **Kanti said:**
> I just got my WUSB54G driver install and when i do NDISWRAPPER-L its said:("Driver install and present") with code xxxx. I try ndiswrapper -m but still don't show up. any I dea?

Did you do these commands?
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

---

### Post by Kanti on 2007-05-04
Yes i did.

---

### Post by Kanti on 2007-05-04
I got it to work now thanks. I think the problem is that i'm using 64Bit version of ubuntu, so i install the 32 bit version and now its working. Thanks.

---

