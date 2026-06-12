---
title: "Ralink 5370 not working"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by dvojas on 2013-11-09
Hello I found many posts here with ralink 5370 not working on ubuntu 13.10. I tried installing the drivers as here but stucked on 

modprobe rt5370sta
```
FATAL: Module rt5370sta not found.
```

here is results from:

lshw -C network
```
*-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA

```

modinfo rt2800usb | grep 5370
```
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*

```

Please help me, I am linux noob.

---

### Post by varunendra on 2013-11-11
Welcome to the forums dvojas !

Looks like a failed compilation of the rt5370sta driver. Which thread or post did you follow to install it? Link please.

Apart from that, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

