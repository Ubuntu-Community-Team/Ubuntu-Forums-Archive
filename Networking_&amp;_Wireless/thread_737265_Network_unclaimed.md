---
title: "Network unclaimed"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by jsaturno on 2008-03-27
Hi, 

I have the sundance module for my ethernet adapter (ubuntu 7.10) and it used to work before some update...

Now it shows *-network UNCLAIMED (not connecting to the internet)

What's that? How can i fix it?

---

### Post by bvidinli on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/207806](https://bugs.launchpad.net/ubuntu/+bug/207806) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				same for me, it was working before update, now not working... here is info:

root@bvidinli-laptop:/home/bvidinli# uname -a
Linux bvidinli-laptop 2.6.24-12-386 #1 Wed Mar 12 22:30:29 UTC 2008 i686 GNU/Linux
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli# ifconfig
eth0 Link encap:Ethernet HWaddr 00:14:38:1e:e5:6b
          inet addr:172.16.50.121 Bcast:172.16.63.255 Mask:255.255.224.0
          inet6 addr: fe80::214:38ff:fe1e:e56b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:92167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:63437374 (60.4 MB) TX bytes:8048726 (7.6 MB)
          Interrupt:16

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:1718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:77593 (75.7 KB) TX bytes:77593 (75.7 KB)

root@bvidinli-laptop:/home/bvidinli# iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

root@bvidinli-laptop:/home/bvidinli#

root@bvidinli-laptop:/home/bvidinli# lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
root@bvidinli-laptop:/home/bvidinli#

any help is welcome,






additional info:

root@bvidinli-laptop:/home/bvidinli# lshw -C network
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:14:38:1e:e5:6b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5751m-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli#
root@bvidinli-laptop:/home/bvidinli# lshw -C network -businfo
Bus info Device Class Description
========================================================
pci@0000:10:00.0 eth0 network NetXtreme BCM5751M Gigabit Ethernet PCI Express
pci@0000:02:04.0 network PRO/Wireless 2200BG Network Connection
root@bvidinli-laptop:/home/bvidinli#

and, when i press wireless button on my laptop (initially on), i do tail -f /var/log/syslog, i got:

Mar 28 00:08:21 bvidinli-laptop kernel: [ 8243.943388] usb 2-2: USB disconnect, address 7
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: HCI dev 0 down
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: Stopping security manager 0
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: Device hci0 has been disabled
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.186939] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0_bluetooth_hci_164100557f').
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: HCI dev 0 unregistered
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: Unregister path: /org/bluez/hci0
Mar 28 00:08:21 bvidinli-laptop hcid[5672]: Device hci0 has been removed
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.419737] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0').
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.422424] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if1').
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.424851] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if2').
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.426295] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if3').
Mar 28 00:08:21 bvidinli-laptop NetworkManager: <debug> [1206655701.428357] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial').
Mar 28 00:08:21 bvidinli-laptop kernel: [ 3298.553073] bluetooth-apple[6110]: segfault at 00000020 eip 08054452 esp bfc9bcd0 error 4

wireless light (blue) turns off.
i press again to turn it on, i got in syslog:

Mar 28 00:09:06 bvidinli-laptop kernel: [ 8301.519533] usb 2-2: new full speed USB device using uhci_hcd and address 8
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.116656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial').
Mar 28 00:09:07 bvidinli-laptop kernel: [ 8301.911421] usb 2-2: configuration #1 chosen from 1 choice
Mar 28 00:09:07 bvidinli-laptop hcid[5672]: HCI dev 0 registered
Mar 28 00:09:07 bvidinli-laptop hcid[5672]: HCI dev 0 up
Mar 28 00:09:07 bvidinli-laptop hcid[5672]: Device hci0 has been added
Mar 28 00:09:07 bvidinli-laptop hcid[5672]: Starting security manager 0
Mar 28 00:09:07 bvidinli-laptop hcid[5672]: Device hci0 has been activated
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.382886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if2').
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.400315] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if1').
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.451335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0').
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.459859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if3').
Mar 28 00:09:07 bvidinli-laptop NetworkManager: <debug> [1206655747.465143] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_11d_noserial_if0_bluetooth_hci_164100557f').

it seems only bluetooth is affected by button...
but is i see in hardware information and lshw , wireless is identified by system... but there is no eth1

any idea ?

---

### Post by bvidinli on 2008-03-27
seems to be solved here: 
[http://ubuntuforums.org/showthread.php?t=736396](http://ubuntuforums.org/showthread.php?t=736396)

---

### Post by jsaturno on 2008-03-27
> **bvidinli said:**
> seems to be solved here: 
[http://ubuntuforums.org/showthread.php?t=736396](http://ubuntuforums.org/showthread.php?t=736396)

This didn't solve anything for me:(

---

### Post by bvidinli on 2008-03-28
when i boot my laptop with previous kernel or a different kernel, my sound and wireless works...
i think this is an issue with latest kernel.... 

currently i have:
bvidinli@bvidinli-laptop:~$ uname -a
Linux bvidinli-laptop 2.6.24-12-generic #1 SMP Wed Mar 12 23:01:54 UTC 2008 i686 GNU/Linux

---

