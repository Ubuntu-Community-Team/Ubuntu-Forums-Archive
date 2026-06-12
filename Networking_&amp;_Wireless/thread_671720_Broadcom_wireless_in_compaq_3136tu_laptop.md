---
title: "Broadcom wireless in compaq 3136tu laptop"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by in_flu_ence on 2008-01-18
It works perfectly with the restricted driver manager provided. However, the wireless is dropped (not sure if it is the hardware or the software) whenever I make a restart. The wireless indicator on my laptop turns orange (indicating that it is switched off even though the switch is physically switched to on.) 

I think the driver has loaded properly but it is just that the system doesn't register that the switch is physically on. Therefore, I need to physically switch the wireless off and turn it back on again to get the wireless switched on.

Any similar experience?

Thanks

---

### Post by Floppyjoe on 2008-01-18
> **in_flu_ence said:**
> It works perfectly with the restricted driver manager provided. However, the wireless is dropped (not sure if it is the hardware or the software) whenever I make a restart. The wireless indicator on my laptop turns orange (indicating that it is switched off even though the switch is physically switched to on.) 

I think the driver has loaded properly but it is just that the system doesn't register that the switch is physically on. Therefore, I need to physically switch the wireless off and turn it back on again to get the wireless switched on.

Any similar experience?

Thanks
What is your wireless card?

```
lspci
```

I had similar trouble with a broadcom 4318 card on my laptop. Only no problem with the light but it would drop out occasionally with the restricted driver.

---

### Post by in_flu_ence on 2008-01-19
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

That's what i have for lspci

---

