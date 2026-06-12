---
title: "No more connection (at all) and no more System Settings"
date: 2020-05-23
forum: Networking &amp; Wireless
---

### Post by zlotz2 on 2020-05-23
Hi all


Runing the command "sudo lshw -C network" results in DISABLED for Ethernet and Wireless.

More worrisome : no more way to open System Settings or the interface to choose a connection.


KR
Marc

---

### Post by TheFu on 2020-05-23
Please post the relevent output from **lshw** here.

---

### Post by zlotz2 on 2020-05-23
Here is the output of sudo lshw -C connect (I guess it's the relevant output) :

  > -network DISABLED        
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: enp3s0f1
       version: 12
       serial: 80:fa:5b:2f:da:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 latency=0 link=no multicast=yes
       resources: irq:16 ioport:d000(size=256) memory:df214000-df214fff memory:df210000-df213fff
  *-network DISABLED
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 81
       serial: 00:db:df:b2:8c:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-51-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:133 memory:df100000-df101fff


---

### Post by CelticWarrior on 2020-05-23
"Disabled" instead of "Unclaimed" means it's probably disabled in BIOS/UEFI. "Unclaimed" would mean "without drivers" but both are natively supported so it's definitely not that.

>  More worrisome : no more way to open System Settings or the interface to choose a connection.

Please describe what have you been up to just before the catastrophic events.

---

### Post by TheFu on 2020-05-23
Both have drivers according to that output. That's good.

I'd plug in the ethernet and see if that worked.  Then I'd check the BIOS as CW says.  Some laptops have physical switches that need to be slide.  I have a Dell like that.  If I see red under the switch location, wifi is physically disconnected.

For other laptops, there is a Fn+<some key> to toggle networking/wifi.  IDK if this is a BIOS toggle or an OS toggle.  For the wifi, in the OS there's a tool called **rfkill**. This can be used to disable or lock bluetooth and wifi hardware instead of the BIOS. This can be much more convenient.  rfkill is only for wireless, not for the ethernet.

---

