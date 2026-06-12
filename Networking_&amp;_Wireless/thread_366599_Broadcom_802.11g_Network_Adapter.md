---
title: "Broadcom 802.11g Network Adapter"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by brokencrystal on 2007-02-21
I bought a Dell Inspiron 1501 and cannot get the wireless to work in Ubuntu Edgy.  I tried the Windws driver with ndiswrapper, but no luck.  The Windows Vista Device Manager identifies it as Broadcom 802.11g Network Adapter.  Any ideas?

---

### Post by chili555 on 2007-02-21
Sure! Jump back into Edgy and open a terminal. Issue the command lspci and note carefully the part about the network controller. You will need all this information to proceed. Here, for example, is mine:```
03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

You will see exactly the Broadcom chipset you have, there are a few, and no one driver works for all. Once you have that, you can do a search in this forum and you will see quite a few posts about getting the Broadcom bcm-xyz-whatever going. Just follow in the footsteps of those pioneers who have blazed the trail for you.

What went wrong when you tried ndiswrapper?

Post back if you get stuck. Good luck.

---

