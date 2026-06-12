---
title: "Ethernet connection not workin"
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by clarence-simard on 2016-03-16
Hi,

   ethernet connection is not working on my Lenovo x230 laptop. I have dual boot and ethernet works fine on Windows and wifi works correctly on Ubuntu. I tried a few solutions here and there but nothing work so far. One of the thing I tired is to set "managed=true" in the file /etc/NetworkManager/NetworkManager.conf, but not result. I would appreciate some help now. 

Thanks

Here some informations
**lshw -c network**
```
  *-network                      description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:59:10:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 84:3a:4b:05:d7:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-79-generic firmware=18.168.6.1 ip=192.168.0.165 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f1c00000-f1c01fff



```

[B]Content of file /etc/network/interfaces:
[/B]```

auto lo
iface lo inet loopback

```

---

### Post by michi1983 on 2016-03-16
Hi,

did you set up anything in the Network Manger of Ubuntu or is the NIC not showing at all?

You could try to edit your /etc/network/interfaces file to
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

After the edit do a ```
sudo /etc/init.d/networking restart
```
and see if the interface comes up.

I also found this link on this forum which should also help you:
[http://ubuntuforums.org/showthread.php?t=2167864](http://ubuntuforums.org/showthread.php?t=2167864)

---

### Post by clarence-simard on 2016-03-21
> **michi1983 said:**
> Hi,

did you set up anything in the Network Manger of Ubuntu or is the NIC not showing at all?

You could try to edit your /etc/network/interfaces file to
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```


Hi Michi,
             you found the solution, thanks. Sorry it took so long to answer, I was out of town and could not try your solution. 

Reminder (to myself and everyone): Always backup configuration files when you modify something.

---

