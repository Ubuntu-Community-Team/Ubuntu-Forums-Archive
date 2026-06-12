---
title: "bcm 4318 headache :["
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by rdk on 2008-11-27
hi all

just upgraded to 8.10.. very happy about it but as with previous releases my wifi is dead :[

connected over wire with no probs whatsoever.. downloaded all updates.. and only then i saw driver to my card in 'hardware drivers'.. activated it.. rebooted.. and still nothing :[ cant c any networks :[

will greatly appreciate any help since i'm little bit lost what to do for the moment..

thanks
r

---

### Post by Ayuthia on 2008-11-28
Can you post the results of:
```
lspci -nn
lshw -C network
```

What were you using in the previous versions?

---

### Post by superprash2003 on 2008-11-28
also output of 
iwconfig

---

