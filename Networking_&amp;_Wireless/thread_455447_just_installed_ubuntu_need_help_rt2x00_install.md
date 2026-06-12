---
title: "just installed ubuntu need help rt2x00 install"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by exel420 on 2007-05-26
I just installed ubuntu on one of my computers and I'm totally new to Linux and am trying to get my wireless card to work i downloaded the drivers i need rt2x00-2.0.0-b3. I am trying to install the drivers and i read some posts about it and am trying to install it but everytime i get to $make rt2x00-install it says there are is no file. I have spent almost a whole day working on this with no success. Any advice or help is greatly appreciated

---

### Post by ruy_lopez on 2007-05-26
Try this:

```
sudo modprobe rt[then press tab instead of return]
```

it should show you a list of supported rt2xx  modules. Remember the name of the one which closest matches your card. Then do this:

```
sudo modprobe rt2xxx
```

where rt2xxx is the one you remembered from the previous step.

---

