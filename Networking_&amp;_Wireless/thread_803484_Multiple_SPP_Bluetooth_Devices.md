---
title: "Multiple SPP Bluetooth Devices"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by lionclaw on 2008-05-22
I'm trying, rather unsuccessfully, to get multiple bluetooth devices working with Ubuntu 8.04.  I'm using a cell phone for internet access (rfcomm0) and am trying to use several devices which use SPP.  They all work on their own, but none of them seem to be able to connect at the same time.  When I try to connect a second device I get "Can't connect RFCOMM socket: Too many links"

I'm using a Cirago BT 2.0 dongle.

Any ideas?

Here's my rfcomm.conf

```
rfcomm0 {
        bind yes;
        device 00:15:B9:80:9A:C5;
        channel 4;
        comment "Bluetooth PPP Connection";
}

rfcomm4 {
	bind yes;
	device 00:06:66:00:D4:23;
	channel 1;
	comment "Serial Port";
}

rfcomm5 {
	bind yes;
	device 00:06:66:00:D4:38;
	channel 1;
	comment "Serial Port";
}
```

Thanks!

Andy

---

### Post by lionclaw on 2008-06-03
Still looking for a solution.

---

### Post by scanman717 on 2009-01-26
Hey lionclaw.. Was wondering if you ever got this to work??  I can't even get one device to connect..  Are you using a BlueSnapXP by chance?? MAC looks similar.

Thanks

---

