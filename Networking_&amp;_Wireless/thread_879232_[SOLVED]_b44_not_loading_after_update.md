---
title: "[SOLVED] b44 not loading after update"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by PinkFloyd102489 on 2008-08-03
I just installed from the hardy-proposed, since bcm4328 is supposedly supported under the new restricted modules. I got it working but have a new problem. My ethernet adapter wont work and the b44 module wont load. It gives this error:

```
FATAL: Error inserting b44 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg gives:

```
[  129.854768] b44: disagrees about version of symbol ssb_device_is_enabled
[  129.854780] b44: Unknown symbol ssb_device_is_enabled
[  129.854835] b44: disagrees about version of symbol ssb_pcicore_dev_irqvecs_enable
[  129.854840] b44: Unknown symbol ssb_pcicore_dev_irqvecs_enable
[  129.854960] b44: disagrees about version of symbol ssb_bus_may_powerdown
[  129.854964] b44: Unknown symbol ssb_bus_may_powerdown
[  129.855113] b44: disagrees about version of symbol ssb_pcihost_register
[  129.855116] b44: Unknown symbol ssb_pcihost_register
[  129.855370] b44: disagrees about version of symbol ssb_dma_set_mask
[  129.855374] b44: Unknown symbol ssb_dma_set_mask
[  129.855534] b44: disagrees about version of symbol ssb_device_enable
[  129.855538] b44: Unknown symbol ssb_device_enable
[  129.855738] b44: disagrees about version of symbol ssb_driver_unregister
[  129.855742] b44: Unknown symbol ssb_driver_unregister
[  129.855871] b44: disagrees about version of symbol __ssb_driver_register
[  129.855875] b44: Unknown symbol __ssb_driver_register
[  129.855966] b44: disagrees about version of symbol ssb_bus_powerup
[  129.855970] b44: Unknown symbol ssb_bus_powerup
[  129.856257] b44: disagrees about version of symbol ssb_clockspeed
[  129.856261] b44: Unknown symbol ssb_clockspeed
[  129.856331] b44: disagrees about version of symbol ssb_dma_translation
[  129.856335] b44: Unknown symbol ssb_dma_translation
[  130.410025] NET: Registered protocol family 17
[  131.235001] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  136.541867] wlan0: no IPv6 routers present
[  189.424407] b44: disagrees about version of symbol ssb_device_is_enabled
[  189.424417] b44: Unknown symbol ssb_device_is_enabled
[  189.424473] b44: disagrees about version of symbol ssb_pcicore_dev_irqvecs_enable
[  189.424477] b44: Unknown symbol ssb_pcicore_dev_irqvecs_enable
[  189.424598] b44: disagrees about version of symbol ssb_bus_may_powerdown
[  189.424602] b44: Unknown symbol ssb_bus_may_powerdown
[  189.424751] b44: disagrees about version of symbol ssb_pcihost_register
[  189.424755] b44: Unknown symbol ssb_pcihost_register
[  189.425008] b44: disagrees about version of symbol ssb_dma_set_mask
[  189.425012] b44: Unknown symbol ssb_dma_set_mask
[  189.425180] b44: disagrees about version of symbol ssb_device_enable
[  189.425184] b44: Unknown symbol ssb_device_enable
[  189.425385] b44: disagrees about version of symbol ssb_driver_unregister
[  189.425389] b44: Unknown symbol ssb_driver_unregister
[  189.425518] b44: disagrees about version of symbol __ssb_driver_register
[  189.425522] b44: Unknown symbol __ssb_driver_register
[  189.425614] b44: disagrees about version of symbol ssb_bus_powerup
[  189.425618] b44: Unknown symbol ssb_bus_powerup
[  189.425900] b44: disagrees about version of symbol ssb_clockspeed
[  189.425904] b44: Unknown symbol ssb_clockspeed
[  189.425975] b44: disagrees about version of symbol ssb_dma_translation
[  189.425979] b44: Unknown symbol ssb_dma_translation
```



EDIT: Got it working again. The kernel didnt upgrade it just installed a few updates which broke the module for some reason. Upgrading to the -20 kernel fixed it.

---

### Post by gmstalk on 2008-11-07
I have this problem on  2.6.27-7-generic. How can I reinstall?

---

### Post by gmstalk on 2008-11-30
This is fixed in 2.6.27-8. I went to system> administration> software sources, on the updates tab, I chose pre-released updates (intrepid-proposed). Then I ran the update manager and let it rip.

---

### Post by keogh24 on 2008-12-01
I've upgrated from 8.04 adn I have the 2.6.27-9-generic kernel and still have this problem :S, any suggest?

Regards

---

### Post by keogh24 on 2008-12-02
> **gmstalk said:**
> This is fixed in 2.6.27-8. I went to system> administration> software sources, on the updates tab, I chose pre-released updates (intrepid-proposed). Then I ran the update manager and let it rip.

I tried this and update my kernel from 2.6.27-9 to 2.6..27-10, and the problem was fixed, the b44 module load correctly, but now the wireless is dead, the driver for the wireless is not loaded :S, someone can help me?

Regards

---

### Post by capiscuas on 2009-01-17
The package that gives problems is linux-backports-modules-2.6.27-9-generic

If you depend on that package (for example your wifi driver needs it), then you need to upgrade the kernel, in my case I added the "proposed" repositories on my intrepid apt sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse #Added by software-properties

and I installed the linux-backports-modules-2.6.27-11-generic and I got my eth0 back, and my wlan0 still working.:popcorn:

Best Regards

---

