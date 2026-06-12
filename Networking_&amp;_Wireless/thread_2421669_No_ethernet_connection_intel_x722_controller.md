---
title: "No ethernet connection intel x722 controller"
date: 2019-06-25
forum: Networking &amp; Wireless
---

### Post by brendand2 on 2019-06-25
I was trying to install 18.04.2 server from USB, but the onboard NIC would not connect, so I started trying to diagnose from a 19.04 live USB(was hoping later version might have issue resolved). The only thing I see is that lspci lists the controller as X722 while modinfo lists the driver as XL710. Please find the details below. Intel Support was of no help. It is interesting how they only support licensed distros. Thanks.

```
$ uname -a
Linux ubuntu-mate 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


$ lspci
1a:00.0 Ethernet controller: Intel Corporation Ethernet Connection X722 for 10GBASE-T (rev 09)
1a:00.1 Ethernet controller: Intel Corporation Ethernet Connection X722 for 10GBASE-T (rev 09)


$ lshw
              *-network:0
                   description: Ethernet interface
                   product: Ethernet Connection X722 for 10GBASE-T
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:1a:00.0
                   logical name: eno0
                   version: 09
                   serial: xx:yy:zz:aa:bb:c2
                   capacity: 10Gbit/s
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pm msi msix pciexpress vpd bus_master cap_list rom ethernet physical 1000bt-fd 10000bt-fd autonegotiation
                   configuration: autonegotiation=off broadcast=yes driver=i40e driverversion=2.7.6-k firmware=3.33 0x80000f52 1.1824.0 latency=0 link=no multicast=yes
                   resources: irq:30 memory:9f000000-9fffffff memory:a0808000-a080ffff memory:a0980000-a09fffff memory:a0400000-a07fffff memory:a0890000-a090ffff
              *-network:1
                   description: Ethernet interface
                   product: Ethernet Connection X722 for 10GBASE-T
                   vendor: Intel Corporation
                   physical id: 0.1
                   bus info: pci@0000:1a:00.1
                   logical name: enp26s0f1
                   version: 09
                   serial: xx:yy:zz:aa:bb:c3
                   capacity: 10Gbit/s
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pm msi msix pciexpress vpd bus_master cap_list ethernet physical 1000bt-fd 10000bt-fd autonegotiation
                   configuration: autonegotiation=off broadcast=yes driver=i40e driverversion=2.7.6-k firmware=3.33 0x80000f52 1.1824.0 latency=0 link=no multicast=yes
                   resources: irq:30 memory:9e000000-9effffff memory:a0800000-a0807fff memory:a0000000-a03fffff memory:a0810000-a088ffff


$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

$ modinfo i40e
filename:       /lib/modules/5.0.0-13-generic/kernel/drivers/net/ethernet/intel/i40e/i40e.ko
version:        2.7.6-k
license:        GPL v2
description:    Intel(R) Ethernet Connection XL710 Network Driver
author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
srcversion:     4353F7C1D33280CD88BAE8F




```

---

### Post by chili555 on 2019-06-25
What method have you used to try to connect? To which port is the known working ethernet cable attached. Please try:```
sudo dhclient -v eno0
```If there is no connection, switch the cable and try again.

The -v for verbose should produce some output that helps us understand what happens (or doesn't) when trying to connect.

Once we get connected, we'll amend the netplan file to make it persistent.

---

### Post by brendand2 on 2019-06-26
```
$ sudo dhclient -v eno0Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Cannot find device "eno0"
Error getting hardware address for "eno0": No such device


If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at www.isc.org or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..


exiting.
```
I tried both ethernet ports. Intel Support did say > [COLOR=#555555][FONT=intel-clear]We currently do not have network drivers available for Ubuntu 18.04.2 server [/FONT][/COLOR] which makes no sense to me. I also tried CentOS since Intel claims RedHat is 100% supported. It did not work either.

 I think I am going to install the non-live server so I can skip the network step and then compile and install the drivers myself, a first for me...

---

### Post by chili555 on 2019-06-26
I don't understand at all:

```
*-network:0
                   description: Ethernet interface
                   product: Ethernet Connection X722 for 10GBASE-T
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:1a:00.0
                   logical name: **[COLOR="#FF0000"]eno0[/COLOR]**
                   version: 09
                   serial: xx:yy:zz:aa:bb:c2
                   capacity: 10Gbit/s
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pm msi msix pciexpress vpd bus_master cap_list rom ethernet physical 1000bt-fd 10000bt-fd autonegotiation
                   configuration: autonegotiation=off broadcast=yes **[COLOR="#FF0000"]driver=i40e[/COLOR]** driverversion=2.7.6-k firmware=3.33 0x80000f52 1.1824.0 latency=0 link=no multicast=yes
                   resources: irq:30 memory:9f000000-9fffffff memory:a0808000-a080ffff memory:a0980000-a09fffff memory:a0400000-a07fffff memory:a0890000-a090ffff
```How is it that you now have no eno0 and no driver? What did you do in the interim since you posted the question? Please make sure that you are booted into 19.04 and try again. I don't think the i40e driver made it to 18.04 LTS.

In fact, Intel does have and support the driver:

```
chili@T440p:~$ modinfo i40e
filename:       /lib/modules/5.0.0-17-generic/kernel/drivers/net/ethernet/intel/i40e/i40e.ko
version:        2.7.6-k
license:        GPL v2
description:    Intel(R) Ethernet Connection XL710 Network Driver
[COLOR="#FF0000"]author:         Intel Corporation, <e1000-devel@lists.sourceforge.net>
[/COLOR]
```Their support desk obviously don't know everything we know.

In fact, Intel supports linux very well. Given a choice between network cards, either ethernet or wireless, I, for my own needs, would always choose Intel.

---

### Post by brendand2 on 2019-06-26
Oops. That last time I accidentally booted live 18.04.02. This is the correct output from 19.04 live usb:
```
$ sudo dhclient -v eno0Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/eno0/a4:bf:01:4d:0e:c2
Sending on   LPF/eno0/a4:bf:01:4d:0e:c2
Sending on   Socket/fallback
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 3 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 4 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 11 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 21 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 12 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 7 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 15 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 17 (xid=0x88048154)
DHCPDISCOVER on eno0 to 255.255.255.255 port 67 interval 16 (xid=0x88048154)
.
.
.
```
I tried both LAN ports with the same result.

EDIT: Turns out the LAN drop it was plugged into has stopped working. Thanks for your help. Onwards to server 19.04 install...
EDIT2: Worth commenting that the XL710 driver is the same i40e driver as for the X722, just in case someone ever googles this.

---

### Post by chili555 on 2019-06-26
Ahh! Glad it's working!

---

