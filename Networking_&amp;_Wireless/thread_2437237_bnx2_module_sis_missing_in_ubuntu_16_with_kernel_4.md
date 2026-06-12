---
title: "bnx2 module sis missing in ubuntu 16 with kernel 4.8.0-56"
date: 2020-02-20
forum: Networking &amp; Wireless
---

### Post by sam-alekseev on 2020-02-20
Hi

I upgraded the server dell r510 to ubuntu 16.04 and then installed kernel 4.8.0-56.
after that I lost my motherboard network card Broadcom BCM5716, I found that there is no module bnx2 in the OS.
I did several attempts to compile the driver but no luck.

Could anybody help me with that?

---

### Post by Frogs Hair on 2020-02-20
Moved to *Networking & Wireless.*

---

### Post by webaake on 2020-02-21
Don't do it. Try different kernels instead. Install the UKUU utilty. Here: [http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/)

And chose from the list within Ukuu. Not all those kernels will be appropriate for your needs, but some will.

---

### Post by chili555 on 2020-02-21
> 
and then installed kernel 4.8.0-56.
How, exactly? Are there other supporting packages, extras, modules, headers, etc. that you failed to include?

---

