---
title: "I can't connect to WPA wireless networks"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by matthorr on 2008-05-03
I just got my wireless card to work in Hardy following Alex's instructions in the Broadcom wireless setup for Hardy (step by step).

I can now connect but only to unsecured networks - when I try to connect to my WPA network, Network Manager just spins, never connecting to showing any green dots or blue bars.  WPA_Supplicant is installed...

Any suggestions?

Thanks.

---

### Post by Paris Heng on 2008-05-04
> **matthorr said:**
> I just got my wireless card to work in Hardy following Alex's instructions in the Broadcom wireless setup for Hardy (step by step).

I can now connect but only to unsecured networks - when I try to connect to my WPA network, Network Manager just spins, never connecting to showing any green dots or blue bars.  WPA_Supplicant is installed...

Any suggestions?

Thanks.

Configure your WPA_SUPPLICANT files

or

Most practical, use WICD network manager. Just install the WICD. Most of the time it solve the problem.

---

### Post by y@r!c on 2008-06-04
Try to downgrade NetworkManager to the version 0.6.5, which comes with ubuntu 7.10

In my case it is solved problems with connection to the secure networks.

---

