---
title: "WIFI only 300KB/s"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by superyounan1 on 2008-04-19
Anyone with advice? I can download off the internet at about the same speed as off local machines. I have a dell D620:

```

$ lspci -v | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


```

using ndiswrapper for the driver

```

ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

```

and i have ssb blacklisted

I have an old 900MHZ laptop with an exteral USB wifi card using ndiswrapper, and it races laps on the network compared to this thing

---

### Post by Zanthius on 2008-04-19
Hi,

I hate saying me too on forums, but I also have a Dell (Inspiron 9400) which is having the same issue... it looks like it's being limited to 800k in my case.

I'm using a relatively fresh install of 8.04 RC.

---

### Post by superyounan1 on 2008-04-19
> **Zanthius said:**
> Hi,

I hate saying me too on forums, but I also have a Dell (Inspiron 9400) which is having the same issue... it looks like it's being limited to 800k in my case.

I'm using a relatively fresh install of 8.04 RC.

yeah, same here, fresh hardy install.

I'm guessing it has to do with the driver, it'd be nice if a working, native set of drivers were available, or if I was smart enough to write one

---

