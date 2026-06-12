---
title: "MMC.EXE equivalent in Ubuntu?"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by st0nes on 2007-10-12
Hi all,

I am trying to connect to my corporate wifi network.  Their instructions are that I should run mmc.exe (from a windows laptop) to retrieve my authentication certificate.  When I told them I run Linux, they gave me their best blank look and told me to figure it out for myself.  Is there a Linux equivalent of mmc.exe that I can use to get this certificate?  Despite diligent googling, I have been unable to sort this out.  I would be delighted if anyone could assist.  Thanks in advance.

---

### Post by rickyjones on 2007-10-12
It sounds like you need the certificate file from your local Certificate Authority (CA). The security department should be able to provide you the file.

However, it sounds like they require that the network card authenticate the machine to the wireless network using this security certificate. I'm not sure that that can be done in Ubuntu yet.

-Richard

---

### Post by jhernandez1270 on 2007-11-22
I am looking for the same thing...but haven't found anything yet...maybe run mmc.exe under wine???

---

