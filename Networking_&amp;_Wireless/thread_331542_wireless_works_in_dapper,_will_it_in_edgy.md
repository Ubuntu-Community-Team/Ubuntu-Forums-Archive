---
title: "wireless works in dapper, will it in edgy?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by chudder on 2007-01-04
Hi, I've been using a centrino duo (not core or 2) on dapper and wireless has been working fine.  I want to upgrade to edgy, but I want to find out if anyone has ever done that and no longer got wireless after the install of edgy? with specs of:

intel centrino duo
toshiba satellite a105-s4074

I will most likely download and roll the version up.  I know people have lost wireless when using the CD.  

Thank you very much for any hints.

Chud

---

### Post by haiku99 on 2007-01-04
You need to say what type, make and model of wifi adapter you have to get a better idea, but FWIW my internal Broadcom 4311 and external Linksys WUSB54G work fine w/ Edgy, as they did w/ Dapper  (did a clean install of Edgy, not an upgrade FWIW)

---

### Post by meng on 2007-01-04
Probably the best indication would be to run the Edgy LiveCD and see if your wireless is still detected and working.

---

### Post by chudder on 2007-01-04
> **haiku99 said:**
> You need to say what type, make and model of wifi adapter you have to get a better idea, but FWIW my internal Broadcom 4311 and external Linksys WUSB54G work fine w/ Edgy, as they did w/ Dapper  (did a clean install of Edgy, not an upgrade FWIW)

I imagine I need to type:

```
 sudo lspci 
```

then it will display my hardware
which one is it?

Thanx

And Thank you meng for the tip on running the CD, I might try if I get a hold of one any time soon.

---

### Post by chudder on 2007-01-04
> **haiku99 said:**
> You need to say what type, make and model of wifi adapter you have to get a better idea, but FWIW my internal Broadcom 4311 and external Linksys WUSB54G work fine w/ Edgy, as they did w/ Dapper  (did a clean install of Edgy, not an upgrade FWIW)

These are two devices that I think could be it.  If they're not let me know.  Thanks

```
0000:05:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:07:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)

```

---

