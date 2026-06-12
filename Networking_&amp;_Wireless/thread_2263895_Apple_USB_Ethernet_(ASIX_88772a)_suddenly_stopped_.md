---
title: "Apple USB Ethernet (ASIX 88772a) suddenly stopped working"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by primoze on 2015-02-04
Hi.

I have a Dell XPS 13 with Xubuntu 14.04 installed. Since it doesn't have an ethernet port I'm using Apple's ethernet dongle. It was working fine, up until yesterday, when it suddenly stopped, and it refuses to connect again.
I have downloaded the latest asix drivers, but it didn't help.

I should mention that the dongle is plugged into my display, and that plugged into my computers USB port, but that shouldn't make a difference.

Result of uname -a
```
Linux silverpad 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Result of the wireless_script:
[http://paste.ubuntu.com/10050246/](http://paste.ubuntu.com/10050246/)

Output of dmesg | tail -n 20
```
[ 2104.492522] usb 2-2.4.2: new high-speed USB device number 12 using xhci_hcd
[ 2104.527142] usb 2-2.4.2: New USB device found, idVendor=05ac, idProduct=1402
[ 2104.527151] usb 2-2.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2104.527156] usb 2-2.4.2: Product: Apple USB Ethernet Adapter
[ 2104.527160] usb 2-2.4.2: Manufacturer: Apple Inc.      
[ 2104.527164] usb 2-2.4.2: SerialNumber: 2BEA03
[ 2104.528936] ASIX USB Ethernet Adapter:v4.16.0 09:03:35 Feb  4 2015
[ 2104.528936]     http://www.asix.com.tw
[ 2105.193362] eth%d: status ep1in, 8 bytes period 11
[ 2105.193722] eth0: register 'asix' at usb-0000:00:14.0-2.4.2, ASIX AX88772A USB 2.0 Ethernet, 78:31:c1:f2:04:39
[ 2105.229074] eth0: rxqlen 0 --> 10
[ 2105.229087] eth0: rxqlen 10 --> 20
[ 2105.229100] eth0: rxqlen 20 --> 30
[ 2105.229110] eth0: rxqlen 30 --> 40
[ 2105.229114] eth0: rxqlen 40 --> 44
[ 2105.318957] eth0: ax88772a - Link status is: 0
[ 2110.088527] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```


Result of ifconfig
```
eth0      Link encap:Ethernet  HWaddr 78:31:c1:f2:04:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:282 (282.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 78:31:c1:f2:04:39  
          inet addr:169.254.6.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


```

This is urgent, so help is highly appreciated.

---

### Post by chili555 on 2015-02-04
I downloaded the driver file as well. The *readme* says, in part, "This driver has been verified on kernel versions from 2.6.14 to 3.8.0." You are using kernel version 3.13. There is no chance this will compile on 3.13, at least using any method I am aware of. I noticed this in the driver included in Ubuntu:> $ modinfo asix
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/usb/asix.ko
license:        GPL
description:    ASIX AX8817X based USB 2.0 Ethernet Devices
[COLOR="#FF0000"]version:        22-Dec-2011[/COLOR]
author:         David Hollis
srcversion:     8F87AA2A263EBAE820B3CA7
<snip>I suspect the driver has had little or no attention for quite a while.

You might try rebooting into an earlier kernel version at the GRUB menu to see if it works as expected. You might also try a newer, better supported device.

I wish my answer could be better.

---

### Post by primoze on 2015-02-04
> **chili555 said:**
> There is no chance this will compile on 3.13, at least using any method I am aware of.

The compile and install didn't give me any errors. I'm assuming (HA!) the build would error if there were problems.

> **chili555 said:**
> You might try rebooting into an earlier kernel version at the GRUB menu to see if it works as expected. You might also try a newer, better supported device.

Nice. Just last week my root partition became full, so I removed all of the old kernel versions :( I guess this will teach me to keep a few latest ones around, huh?

As for another device: any suggestions? Preferably something that can be picked up in any computer store.

One thing I don't get is how could it have suddenly stopped working. I literally unplugged the display port and display USB and when plugging them back in trouble began. I didn't even reboot the machine in between. Argh...
Anyway, hopefully I didn't turn a solvable situation into an unsolvable one with the new driver...

Thanks.

---

### Post by chili555 on 2015-02-04
I doubt you did anything with the driver. It won't compile, it won't install and so it won't interfere. It will frustrate, however!

You might look here: [http://www.reddit.com/r/Ubuntu/comments/1vmad6/any_usbethernet_adapter_you_know_it_works_good/](http://www.reddit.com/r/Ubuntu/comments/1vmad6/any_usbethernet_adapter_you_know_it_works_good/)

I suppose it is possible that the device broke.

---

### Post by primoze on 2015-02-05
> **chili555 said:**
> I suppose it is possible that the device broke.

Nope. I tried another one (new), same thing. I'm gonna try with a new one tomorrow. It has the AX88179 chipset, the driver for which was last updated May 2014, and the docs say 3.8 or later, IIRC.

---

### Post by chili555 on 2015-02-05
> **primoze said:**
> Nope. I tried another one (new), same thing. I'm gonna try with a new one tomorrow. It has the AX88179 chipset, the driver for which was last updated May 2014, and the docs say 3.8 or later, IIRC.I assume you refer to this:```
$ modinfo ax88179_178a 
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/usb/ax88179_178a.ko
license:        GPL
description:    ASIX AX88179/178A based USB 3.0/2.0 Gigabit Ethernet Devices
srcversion:     76A3B8EBD187A8970B310F9
alias:          usb:v17EFp304Bd*dc*dsc*dp*ic*isc*ip*in*
<snip>
```Please keep us posted. The searchers will appreciate it.

---

