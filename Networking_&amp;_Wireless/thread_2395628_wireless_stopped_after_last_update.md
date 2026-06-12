---
title: "wireless stopped after last update"
date: 2018-07-04
forum: Networking &amp; Wireless
---

### Post by simon114 on 2018-07-04
I have rum the command 
```
sudo lshw -C network 
```
And the result is
```
 *-network                      description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 07
       serial: 00:8c:fa:82:d4:05
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.20 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:34 ioport:2000(size=256) memory:f1000000-f1000fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f2b00000-f2b07fff

```

I have also purged as follows

```
[COLOR=#111111][FONT=Consolas]sudo apt purge bcmwl-kernel-source[/FONT][/COLOR]
```

and reinstalled 

```
[COLOR=#111111][FONT=Consolas]sudo apt update[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]sudo apt install bcmwl-kernel-source[/FONT][/COLOR]
```

and rebooted

Ethernet network is greyed out

any help please, thanks

---

### Post by jeremy31 on 2018-07-04
Using Ubuntu 16.04 and a 4.15 kernel ```
uname -a
```

---

### Post by simon114 on 2018-07-04
so how should i proceed?

I have just done
```
apt-cache search linux-image
```

which one should I choose?

Thanks for the help

---

### Post by simon114 on 2018-07-04
I have now accessed the grub menu from boot by holding shift key down and chosen Advanced options, and booted with kernel 4.13 generic, but still the wireless adapter doesn't work

---

### Post by simon114 on 2018-07-04
I reverted to 4.13 by pressing shift on boot, (actually had to esc on purple screen and then shift to get to advanced options

then chose boot 4.13 generic

But then had to uninstall and reinstall wireless drivers as follows

```

sudo apt-get purge bcmwl-kernel-source
sudo apt update
sudo apt-get install bcmwl-kernel-source

```

Hope That helps

I just want to set 4.13 as default now, Time to research again..

---

### Post by jeremy31 on 2018-07-04
Simon114, if you were trying to use the 4.15 kernel, you need a newer version of bcmwl-kernel-source as the Ubuntu 16.04 repositories don't have the needed patches for 4.15 yet

---

### Post by simon114 on 2018-07-04
> **jeremy31 said:**
> Simon114, if you were trying to use the 4.15 kernel, you need a newer version of bcmwl-kernel-source as the Ubuntu 16.04 repositories don't have the needed patches for 4.15 yet


Hi Jeremy31,

Would you be able to describe the process for installing the updated bcmwl-kernel-source for the 4.15 kernel?

Thankyou

---

### Post by jeremy31 on 2018-07-04
Check ```
uname -a
``` if it says  x86_64 x86_64 x86_64 GNU/Linux then download [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb)
Boot into the 4.15 kernel and use terminal to go into the directory that it was downloaded to and ```
sudo dpkg -i bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb
```
Then reboot into the 4.15 kernel

---

