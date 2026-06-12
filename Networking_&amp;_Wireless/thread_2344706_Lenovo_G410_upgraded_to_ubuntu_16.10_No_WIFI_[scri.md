---
title: "Lenovo G410 upgraded to ubuntu 16.10 No WIFI [script result attached]"
date: 2016-11-27
forum: Networking &amp; Wireless
---

### Post by shashanksworld on 2016-11-27
Hi,
I have recently upgraded my system to 16.10; very happy with the build; But I am not able to get the wireless up.
Please find attached: output of the script as asked in other related threads.

[ATTACH]272428[/ATTACH]

Thanks in advance.

-Shashank

---

### Post by chili555 on 2016-11-28
We see no wireless device at all in your wireless info. Is it enabled in the BIOS? Is it broken? Or what??

Please run and post:```
lspci -nnk
```

---

### Post by shashanksworld on 2016-11-28
Please check the output in the file attached.

..
[ATTACH]272445[/ATTACH]

---

### Post by chili555 on 2016-11-28
I'm sorry. There is still no wireless device showing. We cannot suggest a driver for a disabled or faulty device.

---

### Post by jeremy31 on 2016-11-29
Please check your BIOS to see if wifi(WLAN) is enabled as if I disable wifi on my Lenovo G710 in BIOS, it disappears from the lspci results.  You may also need to reset BIOS to defaults

You likely have a Qualcomm Atheros wifi card supported by either ath9k or ath10k_pci

---

