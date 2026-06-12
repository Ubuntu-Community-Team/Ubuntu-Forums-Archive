---
title: "Broadcomm unknown device 167a"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by jon_herr on 2006-08-22
I'm trying to install ubuntu dapper on a dell 360n which has a new broadcomm ethernet nic that apparently isn't supported.

Using lspci I get...
"... Broadcomm ethernet... unknown device 167a"

I've downloaded the driver source from broadcom and copied the new "tg3.ko" in to the drivers folder but the hardware still isn't recognised.

Help?

Thanks,
Jon

---

### Post by jon_herr on 2006-08-22
Refinement:
The device is reported by another linux distribution as a 'bcm5754'

Still isn't working for me in ubuntu.

Thanks in advance,
Jon

---

### Post by jon_herr on 2006-08-24
All,
Well I figured out the problem... 

I recompiled the kernel using the new drivers which are available here:
[http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)

The driver of interest is the 'linux (tg3)' which is version 3.58b
[http://www.broadcom.com/support/ethernet_nic/driver-sla.php?driver=570x-Linux](http://www.broadcom.com/support/ethernet_nic/driver-sla.php?driver=570x-Linux)

Please please please ubuntu team!  Incorporate this newer driver soon!  I'm trying to roll out engineering workstations that have this NIC - there are a lot of eyes on me to have this rollout go smoothly!

Thanks,
Jon

---

### Post by jrasmussen0 on 2006-08-28
I tried to 'modprobe tg3' from the first Dapper CD by mail but it seems to be the wrong version. It loads but doesn't allow me to 'ifup eth0'. 

And there isn't enough packages to build the new driver. I'm going to load another NIC and download a newer kernel to see if that helps. Otherwise, I'll just compile the tg3 driver.

---

