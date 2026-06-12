---
title: "totally newbie, need s help with rtl8180"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by lilmale1 on 2008-08-31
need help with rtl8180 wireless card in ubutu 8. tar.gz file
I notice I need a new admin pass to pass me tru the seen so I refresed my password. and as for sure. I don't know what else to do but extract before i enter su. so what the hell im new please help. !!me!!:popcorn:
i'll be waiting:confused:

oh yeah, i install some kind of compiler and don't know what the hell , help me:guitar:

---

### Post by pytheas22 on 2008-08-31
I don't think that compiling the rtl8180 driver (which I guess you got from a manufacturer's website or something) will work well on the Hardy kernel, and if it does it might be more difficult than you need.  If you post the output of these commands, we can give you easier instructions on getting your card working:
```

lshw -C Network
lspci -nn
```

---

