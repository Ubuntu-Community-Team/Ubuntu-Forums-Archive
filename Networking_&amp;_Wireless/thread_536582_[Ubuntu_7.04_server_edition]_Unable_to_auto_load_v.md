---
title: "[Ubuntu 7.04 server edition] Unable to auto load vmxnet eth0 driver"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by razor7 on 2007-08-27
Hello...i have installed VMWare tools into my Ubuntu 7.04 server on my VMWare 6.0 workstation and the bridged network is not auto configured, each time I reboot, i have to type:
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
modprobe vmxnet
/etc/init.d/networking start

and the bridged network is enabled again...

How can i stop that so it loads automatically?

Thanks in advise...

---

### Post by momohteks on 2007-11-26
up!

---

