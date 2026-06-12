---
title: "3G Connection Error: The connection was not supported by oFono"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by ockac23 on 2015-04-10
Hi folks,

I have ubuntu 14.04.1 LTS 64bit.

When I try to connect to internet using a mobile 3G usb stick I receive the following error message:

**Connection activation failed (32) The connection was not supported by oFono**.

This error did not happen earlier, but since the last few months.

Can you help pls how to resolve this issue?

Thanks

---

### Post by Vladlenin5000 on 2015-04-11
Please contact your service provider.

---

### Post by ockac23 on 2015-04-11
> **Vladlenin5000 said:**
> Please contact your service provider.

You are not serious, are you? :-)


I found the solution:

sudo apt-get purge ofono
sudo apt-get install modemmanager

Works perfectly.


[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

