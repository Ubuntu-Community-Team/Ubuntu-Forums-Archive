---
title: "Azurewave wifi / BT AW-NB159H not recognized"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by frank92 on 2015-01-03
Hi Ubuntu experts,

I have installed Ubuntu 14.04 on my new Gigabyte Brix mini PC. It has a build in wifi / BT module from Azurewave (no AW-NB159H). Unfortunately post installation this modul is not recognised.

Does anyone know if this wifi card is supported. I could not find much on the internet, so I doubt.

I would be grateful for any comment or suggestion

Best Wishes

Frank

---

### Post by Eugenio_Cunha on 2015-06-15
I have the same problem! :( 
Sugestions?

---

### Post by jeremy31 on 2015-06-16
Post the results from the following command in terminal```
lspci -nnk | grep -iA2 net
```
and then we will see what can be done

---

### Post by slickymaster on 2015-06-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

