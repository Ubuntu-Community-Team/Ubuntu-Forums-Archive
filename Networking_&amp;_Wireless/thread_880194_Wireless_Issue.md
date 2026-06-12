---
title: "Wireless Issue"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by MasterNetra on 2008-08-04
For some reason i'm only connecting at about 10% of actual connection speed eg. 5mbps instead of 50mbps. My card type is in my signature. In this case i am connected at 2mbps out 20mbps and i am right next to the wireless signal and no noise i am aware of and it does this elsewhere too. I'm thinking its the driver or something but idk.

Also my labtop is a Dell Latitude D530

---

### Post by pytheas22 on 2008-08-04
With some Broadcom cards there are issues like this on b43, the Broadcom driver used by default in Ubuntu 8.04 (you're using Hardy, right).  Please post the output of these commands so that we know the exact model of your card; with that we can figure out a solution (which will probably be using bcm43xx if it supports your chip, or ndiswrapper otherwise):
```

lspci -nnn
lshw -C Network
```

---

