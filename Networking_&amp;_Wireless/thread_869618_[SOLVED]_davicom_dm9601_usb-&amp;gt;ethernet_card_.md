---
title: "[SOLVED] davicom dm9601 usb-&amp;gt;ethernet card problems"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by afterstep13 on 2008-07-25
I have a davicom dm9601 usb ethernet card.

When i plug in the device, it is detected and drivers are
loaded, but i can't connect to internet using it.

The device fails to get an ip address.

It works perfectly on XP, (same laptop) but not on hardy-32.

Other people seem to have used it with hardy
[http://ubuntuforums.org/showpost.php?p=5440433&postcount=28](http://ubuntuforums.org/showpost.php?p=5440433&postcount=28)

dmesg
[ 1606.469980] usb 3-3: new full speed USB device using ohci_hcd and address 7
[ 1606.714779] usb 3-3: configuration #1 chosen from 1 choice
[ 1606.806122] eth1: register 'dm9601' at usb-0000:00:02.0-3, Davicom DM9601 USB Ethernet, 00:60:6e:00:06:be
[ 1606.912379] eth1: link down
[ 1606.958629] ADDRCONF(NETDEV_UP): eth1: link is not ready

ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:60:6e:00:06:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

i have too do ifconfig eth1 down and then up before i get,

[ 2128.701718] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1

dhclient eth1 gives me,

Listening on LPF/eth1/00:60:6e:00:06:be
Sending on   LPF/eth1/00:60:6e:00:06:be
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

then ifconfig eth1 shows

eth1      Link encap:Ethernet  HWaddr 00:60:6e:00:06:be  
          inet6 addr: fe80::260:6eff:fe00:6be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5239 (5.1 KB)

i think proper drivers are loaded for the deice as

lsusb
Bus 003 Device 008: ID 0a46:9601 Davicom Semiconductor, Inc. DM9601 To Fast Ethernet Adapter

and lsmod | grep net
usbnet                 20232  1 dm9601
mii                     6400  2 dm9601,usbnet
usbcore               146028  8 dm9601,usbnet,uvcvideo,ndiswrapper,usbhid,ohci_hcd,ehci_hcd




I have no idea why it doesnot work, i have been trying for a week
now.

Please help

---

### Post by afterstep13 on 2008-07-27
bump

---

### Post by afterstep13 on 2008-07-27
I finally solved the problem

1. compiled the attached driver 
2. copy it to /lib/modules/2.6*/kernel/drivers/net/usb/dm9601.ko but also backup the old one.
3. it works !

it was caused because, the device wont work in 100Mbps mode, but only in
10Mbps mode. maybe this is because it is usb 1.1

I had to edit the driver source a little to make it work.

Though i guess i have to recompile every time with a kernel update

---

### Post by arun lampard on 2012-11-30
i downloaded the file.. plz help me wer to attach/paste it.. where is the "lib/modules...." be? plz help..

---

### Post by dontogbe on 2013-01-30
Having the same problem... attached file can't unzip... any updates?

---

### Post by äxl on 2013-07-06
This shouldn't be necessary from kernel 2.6.38 upwards.
[URL="http://tech.firdooze.com/2011/11/16/how-to-instal-davicom-9601-drivers-dm9601-on-linux/"]
http://tech.firdooze.com/2011/11/16/how-to-instal-davicom-9601-drivers-dm9601-on-linux/[/URL]
You can get the C file for your running kernel like this:
```
wget -O dm9601.c https://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/plain/drivers/net/usb/dm9601.c?id=refs/tags/v$(uname -r | cut -d"-" -f1)
```

Or try the qf9700 module [http://mquin.livejournal.com/178482.html](http://mquin.livejournal.com/178482.html).

---

