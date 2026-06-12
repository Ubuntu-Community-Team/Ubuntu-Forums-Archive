---
title: "Agere et1310 driver for dapper drake"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by stardust888 on 2008-10-23
Hi,

Anybody was able to get the Agere et1310 ethernet controller to work with dapper drake? Here is what I did:

- download the linux-headers for my kernel version
- download latest et131x src from sourceforge
- build the driver but I get a lot of compilation errors such as:
  IRQF_SHARED, struct vlan_group has no member named vlan_devices_arrays etc.

Anyone was successfull?

Thanks!

---

### Post by stardust888 on 2008-10-23
update:

I was able to compile et1310 driver and install it (following instructions here: [http://ubuntuforums.org/showthread.php?t=276041](http://ubuntuforums.org/showthread.php?t=276041)). Now I can see the hardware recognized with link light but data light is always blinking (weird, eventhough there is no traffic). But I am not able to see any traffic on the interface.

Here are the changes that I did to patch the driver:

1- et131x_initpci.c: 
-    INIT_WORK( &adapter->task, (void (*)(void *))et131x_isr_handler, adapter );
+    INIT_WORK( &adapter->task, et131x_isr_handler );
2- et131x_netdev.c: 
-    result = request_irq( netdev->irq, et131x_isr, SA_SHIRQ, netdev->name, netdev );
+    result = request_irq( netdev->irq, et131x_isr, IRQF_SHARED, netdev->name, netdev );

-        pAdapter->vlgrp->vlan_devices[vid] = NULL;
+        pAdapter->vlgrp->vlan_devices_arrays[vid] = NULL;

Anybody spot anything wrong with this?

Thanks!

---

