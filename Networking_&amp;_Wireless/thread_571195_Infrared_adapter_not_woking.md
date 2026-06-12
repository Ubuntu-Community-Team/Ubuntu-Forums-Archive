---
title: "Infrared adapter not woking"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by titun on 2007-10-09
I bought a Infrared adapter to be connected in the USB port [primarily to transfer photos from my Nokia 6070, as the data cable won't work in ubuntu].

I followed this guide [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto) 

In the step 12, when i tried to load the FIR driver as the instructions say, by doing "sudo modprobe irda0"

This gives me the error : "FATAL: Error inserting nsc_ircc (/lib/modules/2.6.20-16-generic/kernel/drivers/net/irda/nsc-ircc.ko): No such device"

The next step, 13 worked ok.

Should i attach my dmesg here... just asking before attaching because that is full of some other hardware-related error i have not been able to recognise till now.

Please tell me what other things i need to attach here.

---

### Post by ashikahamed on 2007-12-15
Plug in your USB infra red adapter and type the following in terminal  ```
dmesg | tail
```If you find something like 'KingSun/Dazzle IRDA/USB' then please visit the link below for the driver.
[http://palosanto.com/~a_villacis/](http://palosanto.com/~a_villacis/)

---

