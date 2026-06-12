---
title: "modprobe FATAL error"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by KiwiP on 2005-05-24
I have been trying to install a SMC 2802W wireless network card.
I have followed the guidance in the post   "Wireless and the SMC 2802W"  which has gone successfully except for the final instruction "modprobe ndiswrapper".
When I try this a get a FATAL error with the following error

FATAL Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

What can I do to process this last instruction.

Thanks for your help

KiwiP

---

### Post by JonahRowley on 2005-05-24
You must run modprobe as root.  Use **sudo modprobe ndiswrapper** instead.

---

### Post by KiwiP on 2005-05-25
I get the error message doing sudo, or even login as root.

After reviewing the sys logs, it indicates a problem with the driver, si I am going to do some work in that area.

thanks for the advice.

KiwiP \\:D/  \\:D/

---

