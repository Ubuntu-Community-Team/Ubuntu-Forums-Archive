---
title: "Broadcam BCM94311MCG wlan on Hardy Heron"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by mkoxp on 2008-06-27
I have a broadcom BCM94311MCG wlan builin card in my hp laptop. With 7.10 ubuntu, it worked fine, without any extra work. I installed hardy-heron (fresh install) and as expected requires more work. Initially, even the wireless card's blue light didn't light up. After using b43-fwcutter and b43 firmware from [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/), the wireless card is activated (light comes up). But still it does not show any wireless networks and still unable to connect. I use WPA, but I think that's later stage. First no wireless networks is shown. Here is the message that may be useful. [Note: I have a USB wireless card (not shown in any of commands below),that works fine, and I can access wireless networks through that.] I'll appreciate any help.

One message that clicks me where it might be going wrong is: [   50.868067] b43-phy0: Radio hardware status changed to DISABLED (but why?)

```
dmesg
[   49.657443] input: b43-phy0 as /devices/virtual/input/input9
[   49.727193] Bluetooth: Core ver 2.11
[   49.730536] NET: Registered protocol family 31
[   49.730541] Bluetooth: HCI device and connection manager initialized
[   49.730544] Bluetooth: HCI socket layer initialized
[   49.771118] Bluetooth: L2CAP ver 2.9
[   49.771123] Bluetooth: L2CAP socket layer initialized
[   49.791209] Bluetooth: RFCOMM socket layer initialized
[   49.791225] Bluetooth: RFCOMM TTY layer initialized
[   49.791227] Bluetooth: RFCOMM ver 1.8
[   50.021676] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   50.808444] b43-phy0 debug: Chip initialized
[   50.809063] b43-phy0 debug: 32-bit DMA initialized
[   50.829545] Registered led device: b43-phy0:tx
[   50.829773] Registered led device: b43-phy0:rx
[   50.829893] Registered led device: b43-phy0:radio
[   50.829937] b43-phy0 debug: Wireless interface started
[   50.868067] b43-phy0: Radio hardware status changed to DISABLED
[   50.868262] b43-phy0 debug: Adding Interface type 2
[   52.722661] [drm] Initialized drm 1.1.0 20060810
[   52.726489] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.726499] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   52.726586] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   61.925187] NET: Registered protocol family 10
[   61.925628] lo: Disabled Privacy Extensions
[   61.926107] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.926616] ADDRCONF(NETDEV_UP): wlan0: link is not ready


lspci
...
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

lsmod | grep b4
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:8c:a4:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64700 (63.1 KB)  TX bytes:64700 (63.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:5d:ff:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-5D-FF-CF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by mkoxp on 2008-07-09
solved. don't know how, but after restarting few no of times, I got it working.

---

