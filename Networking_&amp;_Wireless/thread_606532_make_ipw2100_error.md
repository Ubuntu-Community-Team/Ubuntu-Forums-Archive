---
title: "make ipw2100 error"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by aakmit on 2007-11-08
hi all,

i have some problem about " make ipw2100" which  error shown below

root@vorawut-desktop:/home/vorawut/Desktop/ipw2100-1.2.0# make

mkdir -p /home/vorawut/Desktop/ipw2100-1.2.0/tmp/.tmp_versions
cp /lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/*.mod /home/vorawut/Desktop/ipw2100-1.2.0/tmp/.tmp_versions
make -C /lib/modules/2.6.20-15-generic/build M=/home/vorawut/Desktop/ipw2100-1.2.0 MODVERDIR=/home/vorawut/Desktop/ipw2100-1.2.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.o
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:138:26: error: linux/config.h: No such file or directory
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘schedule_reset’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:681: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_enable_adapter’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1446: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_disable_adapter’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1581: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_up’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1771: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_down’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1828: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1834: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1839: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_reset_adapter’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1892: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1899: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘isr_indicate_associated’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:1996: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘isr_indicate_rf_kill’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:2096: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:2097: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw_radio_kill_sw’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4208: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4209: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_kill_workqueue’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4348: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4349: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4350: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4351: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:4352: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_hang_check’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6366: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_rf_kill’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6381: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6535:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_alloc_device’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6534: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6534: error: (Each undeclared identifier is reported only once
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6534: error: for each function it appears in.)
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6537:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6539:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6540:55: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6541:49: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c: In function ‘ipw2100_pci_init_one’:
/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.c:6657: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/vorawut/Desktop/ipw2100-1.2.0/ipw2100.o] Error 1
make[1]: *** [_module_/home/vorawut/Desktop/ipw2100-1.2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

i tried to serch in this board but i have not found solution for fix it. Please advice me how can i fix it. 
thank you

---

