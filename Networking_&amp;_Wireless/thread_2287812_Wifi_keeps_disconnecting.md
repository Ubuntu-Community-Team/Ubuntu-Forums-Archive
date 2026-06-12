---
title: "Wifi keeps disconnecting"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by virpo-san on 2015-07-22
Hello


I had a buf in Ubuntu 12.04 where it kept disconnecting me from vertain Wifi routers
What helped were these 4 commands:


```

sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up

```


But now i updated to 14.04 and when i use sudo rmmod -f iwlwifi it returns this error:
```

rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'iwlwifi': Resource temporarily unavailable
rmmod: ERROR: could not remove module iwlwifi: Resource temporarily unavailable

```

I will provide any additional information if you can help me solve this problem, thank you

---

### Post by virpo-san on 2015-07-22
This information may be needed, my wireless card should be:

description: Wireless interface
product: Centrino Wireless-N 2200
vendor: Intel Corporation

---

### Post by virpo-san on 2015-07-22
Ok this helped:

> [COLOR=#111111][FONT=Ubuntu]Instead of removing and loading modules. Create [/FONT][/COLOR]/etc/modprobe.d/iwlwifi.conf[COLOR=#111111][FONT=Ubuntu] with the content: [/FONT][/COLOR]options iwlwifi 11n_disable=1[COLOR=#111111][FONT=Ubuntu] then reboot (you may need to run [/FONT][/COLOR]# update-initramfs -u[COLOR=#111111][FONT=Ubuntu])[/FONT][/COLOR]

---

