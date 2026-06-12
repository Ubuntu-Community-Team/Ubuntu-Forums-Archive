---
title: "Netgear A6210 Wireless"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by nbulischeck on 2015-04-12
I'm aware of two things:

1. Many people struggle with this driver, including me.
2. I am running root.

I am currently following the guide here

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

and it seems more promising than the little to no information that can be found elsewhere.

Then I go to make it and I get the error:
```

/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1694:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;
                                      ^
/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1731:38: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
  struct net_device_ops *pNetDevOps = pNetDev->netdev_ops;

make[2]: *** [/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/root/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-33-generic'
make: *** [LINUX] Error 2
```

Usually I can get more out of a make error, but this one has me a bit confused.

```
root@revolt:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1# 
  871  bzip2 -d 2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2 
  872  ls
  873  tar -x 2010_0709_RT2870_Linux_STA_v2.4.0.1.tar 
  874  cd 2010_0709_RT2870_Linux_STA_v2.4.0.1
  875  vi os/linux/config.mk 
```

Does anyone know how to correct this or are there any alternate solutions to installing the rt2870 driver?

---

### Post by chili555 on 2015-04-12
Installing a vintage 2010 driver on your shiny new 2015 Ubuntu is useless. It will not help whatever is going wrong to install the oldest, creakiest thing you can find. 

In fact, the driver it creates has been replaced by rt2800usb which is installed by default in all recent Ubuntu versions.

Tell us what is wrong and maybe we can find a better way to fix it.

---

### Post by nbulischeck on 2015-04-12
Plug in my shiny new A6210 Netgear External Wifi Card and nothing happens. Not detected on lspci, not in ifconfig, iwconfig, nothing.

---

### Post by chili555 on 2015-04-12
Please open a terminal and run:```
lsusb
```Is this your device?  0846:9053 Please see: [https://wikidevi.com/wiki/Netgear_A6210](https://wikidevi.com/wiki/Netgear_A6210)

It is one of the very few devices for which there is currently no known way to get working in Linux. If you have Windows XP drivers appropriate to your architecture, either 32- or 64-bit, we could try ndiswrapper. You might also consider returning it for a supported device.

---

### Post by nbulischeck on 2015-04-14
root@revolt:~# lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 004: ID 8087:0a2a Intel Corp. 
Bus 003 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 006: ID 5986:066d Acer, Inc 
Bus 003 Device 002: ID 0846:9053 NetGear, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Fantastic... Thanks for your help man.

Bought a Powerline 1200 today, so I'll just use that for now.

---

