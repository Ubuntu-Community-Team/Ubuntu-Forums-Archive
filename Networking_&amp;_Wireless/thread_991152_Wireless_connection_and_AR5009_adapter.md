---
title: "Wireless connection and AR5009 adapter"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Sbarton on 2008-11-23
Hi All! Now I have a laptop which includes the above adapter. The OS is Vista(pre-installed 32bit)and dual booting Ubuntu 8.10 64 bit.
System specs are AMD Turion X2. Wireless is recognised by Vista but not  Ubuntu. I have ndiswrapper installed. I have read some info on forums, but alas I have not understood them. Is this a problem with drivers? Or! Should I install 32bit Ubuntu. Any help in getting this to work would be appreciated.
regards

---

### Post by Olivier2371 on 2008-11-23
I would recommend that you use first 8.04 xi386 instead of 8.10 64 bits.

---

### Post by Sbarton on 2008-11-23
Thanks for reply. This did cross my mind and is something I will definitely consider.
regards

---

### Post by eks on 2008-11-23
Maybe try this before:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

It should work on 64 (only Intrepid). But yes, for a laptop I would advise a 32bit install also.

If you manually tried to install a driver, you might have to unblacklist ath5k on /etc/modprobe.d/

---

### Post by Sbarton on 2008-11-24
Thanks for your replies. I have decided to go with 32 bit 8.04LTS.
After I download and install with (alternate disc) I will try wireless again. So I expect to be back
regards

---

