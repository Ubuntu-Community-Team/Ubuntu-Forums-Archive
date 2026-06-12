---
title: "Update killed my wireless connection"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by tele_mark on 2009-11-26
There was a big update this morning -- about 31 packages, including a kernel update, I think. My kernel version is now 2.6.31-15-generic

Before it, I had a 9.10 on my Dell 1501, and the wireless was working fine. After the update, I lost wireless. 

When I went to System>Administration>Hardware Drivers, the Broadcom STA driver is listed, but when I click Activate, it states it's downloading and installing the driver, but it will not activate.

I searched and found this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and installed the  b43-fwcutter package, and followed the instructions. Now under Hardware Drivers, I have entires for both the original Broadcom STA and the new B43 driver. The B43 apparently activates (the green "LED" next to the driver lights up, but still no wireless.

Any help?

---

### Post by ukripper on 2009-11-26
post output of the following:

```
iwconfig
```

```
lshw -C network
```

---

### Post by tele_mark on 2009-11-26
> **ukripper said:**
> post output of the following:

```
iwconfig
``````
lshw -C network
```

iwconfig:

```
mark@Dell1501:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mark@Dell1501:~$ 

```

lshw -C network:

```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:75:96:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.3 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:c0300000-c0301fff

```

---

### Post by drpjkurian on 2009-11-26
> **tele_mark said:**
> There was a big update this morning -- about 31 packages, including a kernel update, I think. My kernel version is now 2.6.31-15-generic

Before it, I had a 9.10 on my Dell 1501, and the wireless was working fine. After the update, I lost wireless. 

When I went to System>Administration>Hardware Drivers, the Broadcom STA driver is listed, but when I click Activate, it states it's downloading and installing the driver, but it will not activate.

I searched and found this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and installed the  b43-fwcutter package, and followed the instructions. Now under Hardware Drivers, I have entires for both the original Broadcom STA and the new B43 driver. The B43 apparently activates (the green "LED" next to the driver lights up, but still no wireless.

Any help?

Hi Telemark

It can be solved by recompiling your driver for wireless. The command which is given by the above forum member will give you the type of wireless card and thereby the driver required.

If yours is a Atheros wireless card you can visit my thread for recompiling your  Atheros driver

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by tele_mark on 2009-11-26
> **drpjkurian said:**
> Hi Telemark

It can be solved by recompiling your driver for wireless. The command which is given by the above forum member will give you the type of wireless card and thereby the driver required.

If yours is a Atheros wireless card you can visit my thread for recompiling your  Atheros driver

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Yeah, but it worked OK prior to the update this morning. Regardless, is that what the problem is? If so, I'll g in that direction. I think I have a Broadcom card as well.

---

### Post by tele_mark on 2009-11-26
Ok, I just rolled back the kernel to the previous one. I was then able to get the driver working. 

So, am I correct that I have to re-compile a new module for the new kernel -- it won't use the one for the old kernel?

I will try the source from [here ]("http://www.broadcom.com/support/802.11/linux_sta.php")if that is the case, otherwise I'll just use the old kernel for now.

---

### Post by brij on 2009-11-27
Hi

Boot with your new kernel and start syaptic then reinstall(or install) bcmwl-kernel-source and other broadcom drivers

---

### Post by tele_mark on 2009-11-27
OK, I went back to 2.6.31-15, and this time the Broadcom B43 driver was used and everything works. If I select the STA driver, it breaks it again. So, I guess this is "solved".

---

