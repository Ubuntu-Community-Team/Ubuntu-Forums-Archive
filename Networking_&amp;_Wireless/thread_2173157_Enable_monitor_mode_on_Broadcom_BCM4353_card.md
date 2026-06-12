---
title: "Enable monitor mode on Broadcom BCM4353 card"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by banjoo2 on 2013-09-08
Hello.
I am quite new to linux and currently running ubuntu 13.04.

I would like to patch my wireless card driver to be able to enable Monitor Mode.

I followed a tutorial over at aircrack-ng and got stuck pretty fast as i am new to linux.
I was therefore wandering if anyone could explain to me and/or guide me through the process of installing a driver with working monitor mode?
As far as i have understood drivers in linux needs to be patched into the kernel itself? and that would require a total recompile of the whole kernel with the patch included?
Is there an easier way maybe? prepatched drivers/kernels ready for install somewhere?
[h=2]Patching the kernel[/h]  
[LIST]
[*] Download the [bcm43xx inject_nofcs patch]("http://www.latinsud.com/bcm/bcm43xx-injection-linux-2.6.20.patch") for the 2.6.20 kernel.

[*] Place the patch in your kernel sources directory  <--- got stuck here...


[*] Run 'patch -p1 -i bcm43xx-injection-linux-2.6.20.patch'.




[/LIST]

---

### Post by Bucky Ball on 2013-09-08
Welcome.

A heads up: Aircrack-ng is NOT supported on this forum and any threads that are support requests for it or specifically about aircrack will be closed. Don't go there. Thanks.

From the forum Code of Conduct:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

### Post by Bucky Ball on 2013-09-08
Wrong kernel by a long way. You would be running 3.9 version in 13.04 (from memory).

---

### Post by matt_symes on 2013-09-08
Hi

> **banjoo2 said:**
> Hello.
I am quite new to linux and currently running ubuntu 13.04.

I would like to patch my wireless card driver to be able to enable Monitor Mode.


Do you know what driver it is currently using ?

Please post the output of (Copy and paste into the terminal).

```
lspci -nnk | grep -iA2 network
```

It may be an option you can enable.

> 
Download the [bcm43xx inject_nofcs patch]("http://www.latinsud.com/bcm/bcm43xx-injection-linux-2.6.20.patch") for the 2.6.20 kernel.

[LIST]
[/LIST]


From [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

> [COLOR=#333333][FONT=Ubuntu]bcm43xx - Deprecated driver (automatically blacklisted). DO NOT USE. Only included here for completeness.[/FONT][/COLOR]

..and a buckyball pointed out, kernel 2.6.20 is ancient.

My install of 13.04 is using....

```
matthew-S206:/home/matthew % uname -r
3.8.0-29-generic
matthew-S206:/home/matthew %

```

Ditch that tutorial right away as it will not help you.

Kind regards

---

### Post by wildmanne39 on 2013-09-08
Hi, it is best to ask your question here [http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/) forums as this topic is not supported on the ubuntu forum so this thread is closed!
Thanks

---

