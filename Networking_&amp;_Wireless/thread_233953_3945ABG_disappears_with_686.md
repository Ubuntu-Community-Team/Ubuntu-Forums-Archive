---
title: "3945ABG disappears with 686"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by nullview on 2006-08-10
Sorry, you guys are dealing with a total n00b here. My 6.06 install works with fine 3945ABG when booting into 386; but when booting to 686 SMP i lose my 3945ABG. It isn't in the Network manager at all.

Thanks for any help you can offer.

---

### Post by wjp.reg on 2006-08-10
> **nullview said:**
> Sorry, you guys are dealing with a total n00b here. My 6.06 install works with fine 3945ABG when booting into 386; but when booting to 686 SMP i lose my 3945ABG. It isn't in the Network manager at all.

Thanks for any help you can offer.

Doesn't happen here.  i have a Lenovo laptop with Centrino Duo T2400 and a 3945ABG that works fine running

Linux linux-laptop 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

what else can you tell us about your setup?

---

### Post by MarkSheely on 2006-08-10
When you installed the 686 kernel, did you also install the 686-restricted-modules package?  That may be your problem....

--Mark

---

### Post by nullview on 2006-08-11
Thanks, that fixed it :)

Cheers,
Jason

---

