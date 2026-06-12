---
title: "wireless disk or harddrive"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by geomarsh on 2010-08-06
my wireless on ubuntu works when I work by disc.  When I loaded ubuntu on my hard drive the wireless will not work.  Can anyone help. marvell yukon 88E8040 pci e fast ethernet controller on Dell wireless 1397 wlan mini card dell 1545 inspiron
Thank you so much for your help, I appreciate it.  When I boot from the installed ubuntu a terminal window command lshw shows Network Disabled: wireless,2,wlan0,serial#
,ethernet  phys wireless, broadcast=y,multi=y,wireless=IEEE 802.11bg.
Under sys>admn,hardware drvrs = download failed "searching"  (No proprietary drivers are in use on this system"

But when booted from disk it finds Broadcom STA Wireless driver and comes up on the Internet with no trouble.

---

### Post by epsolon77 on 2010-08-06
I am not the expert you are looking for, however you will need to let us know what hardware you have for the real experts to chime in.

---

### Post by S.R on 2010-08-06
Do you know if they are being recognized?

In the terminal run:```
lshw
```

---

### Post by LowSky on 2010-08-06
check to see if it requires a proprietary driver

system> administration > proprietary drivers

---

