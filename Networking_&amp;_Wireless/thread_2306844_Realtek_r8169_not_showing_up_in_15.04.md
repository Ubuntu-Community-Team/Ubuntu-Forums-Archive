---
title: "Realtek r8169 not showing up in 15.04"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by stowelly on 2015-12-19
Hi, I have tried to follow the many different threads on this topic, mostly solutions being manually build and install r8168 from the realtek page. and installing r8168-dkms / blacklisting r8169.

but still my device doesnt show up in xubuntu

here is the pastebin of my network stuff (got from the script in the sticky threads) [http://paste.ubuntu.com/14099373/](http://paste.ubuntu.com/14099373/)

most of it seems to be about my usb wireless stick im currently using

I am a little lost on how to resolve this, any help would be gratefully received! thank you

sudo lshw -C network                                                                                                                                                                                                                1 &#8629;
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:dc00(size=256) memory:fbdff000-fbdff0ff memory:fbd00000-fbd1ffff


&#9581;&#9472;mike@mike-linux ~  
&#9584;&#9472;&#10148;  sudo modprobe -r r8168                                                                                                                                                                                                              1 &#8629;
&#9581;&#9472;mike@mike-linux ~  
&#9584;&#9472;&#10148;  sudo modprobe -r r8169
modprobe: FATAL: Module r8169 not found.

this looks like relevant info also:

 dmesg | grep 8168                                               
[    4.328484] r8168: module verification failed: signature and/or  required key missing - tainting kernel

---

### Post by chili555 on 2015-12-19
> **stowelly said:**
> this looks like relevant info also:

 dmesg | grep 8168                                               
[    4.328484] r8168: module verification failed: signature and/or  required key missing - tainting kernelThat's not relevant at all. 

The driver you installed, r8168 clearly indicates: "This driver should only be used for devices not yet supported by the in-kernel driver r8169." The .conf file lists two devices:```
[/etc/modprobe.d/r8168-dkms.conf]
alias	pci:v0000[COLOR="#FF0000"]1186[/COLOR]d0000[COLOR="#FF0000"]4300[/COLOR]sv00001186sd00004B10bc*sc*i*	r8168
alias	pci:v0000[COLOR="#FF0000"]10EC[/COLOR]d0000[COLOR="#FF0000"]8168[/COLOR]sv*sd*bc*sc*i*			r8168

```Neither is your device:```
Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [[COLOR="#FF0000"]10ec:8169[/COLOR]]
```Therefore, installing it and blacklisting r8169 does no good.

I suggest you remove the needless package:```
sudo apt-get purge r8168-dkms
```Then remove the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the line:```
blacklist r8169
```Proofread carefully, save and close the text editor.

Reboot and run the wireless script again and give us the link.

---

### Post by stowelly on 2015-12-19
Sorry, I got very lost in lots of conflicting info on google.

I have done like you said:

[http://paste.ubuntu.com/14107411/](http://paste.ubuntu.com/14107411/)

it at least shows the correct driver in use now

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at dc00 [size=256]
        Memory at fbdff000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fbd00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169

---

### Post by chili555 on 2015-12-19
Let's see what is happening as it tries to connect. I assume you have a known good cable attached. Please run and post:```
cat /var/log/syslog | grep -e r8169 -e eth1
```

---

### Post by stowelly on 2015-12-19
Excuse lack of formatting. I'm now on mobile via ssh.... ```
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-42-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Wed Feb  4 09:37:53 2015 from localhost
%                                                                       &#9581;&#9472;mike@mike-linux ~/Downloads
&#9584;&#9472;&#10148;  cat /var/log/syslog | grep -e r8169 -e eth1
Dec 19 11:25:39 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 11:25:39 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 11:25:39 mike-linux sh[531]: Unknown interface eth1
Dec 19 11:25:39 mike-linux kernel: [    5.034832] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:25:39 mike-linux kernel: [    5.034907] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 11:25:39 mike-linux kernel: [    5.035201] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90005b8c000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 11:25:39 mike-linux kernel: [    5.035203] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 11:25:39 mike-linux kernel: [    5.035214] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:25:39 mike-linux kernel: [    5.035218] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
Dec 19 11:25:39 mike-linux kernel: [    5.035646] r8169 0000:07:00.0 eth1: RTL8168evl/8111evl at 0xffffc90005b9a000, 50:e5:49:c4:f6:a0, XID 0c900800 IRQ 30
Dec 19 11:25:39 mike-linux kernel: [    5.035648] r8169 0000:07:00.0 eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec 19 11:25:39 mike-linux kernel: [    5.150939] r8169 0000:07:00.0 rename3: renamed from eth1
Dec 19 11:25:39 mike-linux kernel: [    5.247323] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 11:25:39 mike-linux kernel: [    5.339193] r8169 0000:07:00.0 eth0: renamed from rename3
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth1): carrier is OFF
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth1): preparing device
Dec 19 11:25:39 mike-linux NetworkManager[668]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 3)
Dec 19 11:25:39 mike-linux kernel: [    8.739509] r8169 0000:04:00.0 eth1: link down
Dec 19 11:25:39 mike-linux kernel: [    8.845103] r8169 0000:07:00.0 eth0: link down
Dec 19 11:26:55 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 11:26:55 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 11:26:55 mike-linux sh[511]: Unknown interface eth1
Dec 19 11:26:55 mike-linux kernel: [    5.052522] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:26:55 mike-linux kernel: [    5.052586] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 11:26:55 mike-linux kernel: [    5.052841] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90005b8c000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 11:26:55 mike-linux kernel: [    5.052843] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 11:26:55 mike-linux kernel: [    5.052924] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:26:55 mike-linux kernel: [    5.052929] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
Dec 19 11:26:55 mike-linux kernel: [    5.053357] r8169 0000:07:00.0 eth1: RTL8168evl/8111evl at 0xffffc90005b9c000, 50:e5:49:c4:f6:a0, XID 0c900800 IRQ 31
Dec 19 11:26:55 mike-linux kernel: [    5.053359] r8169 0000:07:00.0 eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Dec 19 11:26:55 mike-linux kernel: [    5.149207] r8169 0000:07:00.0 rename3: renamed from eth1
Dec 19 11:26:55 mike-linux kernel: [    5.175219] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 11:26:55 mike-linux kernel: [    5.255351] r8169 0000:07:00.0 eth0: renamed from rename3
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth1): carrier is OFF
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth1): preparing device
Dec 19 11:26:55 mike-linux kernel: [    8.779522] r8169 0000:04:00.0 eth1: link down
Dec 19 11:26:55 mike-linux kernel: [    8.779537] r8169 0000:04:00.0 eth1: link down
Dec 19 11:26:55 mike-linux NetworkManager[674]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 3)
Dec 19 11:26:55 mike-linux kernel: [    8.901058] r8169 0000:07:00.0 eth0: link down
Dec 19 11:34:42 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 11:34:42 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 11:34:42 mike-linux sh[524]: Unknown interface eth1
Dec 19 11:34:42 mike-linux kernel: [    0.823805] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:34:42 mike-linux kernel: [    0.823931] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 11:34:42 mike-linux kernel: [    0.824185] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90005b8e000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 11:34:42 mike-linux kernel: [    0.824187] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 11:34:42 mike-linux kernel: [    5.079889] r8168 0000:07:00.0 rename3: renamed from eth1
Dec 19 11:34:42 mike-linux kernel: [    5.147120] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> (eth1): carrier is OFF
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 11:34:42 mike-linux NetworkManager[654]: <info> (eth1): preparing device
Dec 19 11:34:42 mike-linux kernel: [    8.947349] r8169 0000:04:00.0 eth1: link down
Dec 19 11:34:42 mike-linux kernel: [    8.947373] r8169 0000:04:00.0 eth1: link down
Dec 19 11:39:14 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 11:39:14 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 11:39:14 mike-linux sh[518]: Unknown interface eth1
Dec 19 11:39:14 mike-linux kernel: [    0.825346] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:39:14 mike-linux kernel: [    0.825479] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 11:39:14 mike-linux kernel: [    0.826061] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90005b7e000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 11:39:14 mike-linux kernel: [    0.826063] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 11:39:14 mike-linux kernel: [    5.061284] r8168 0000:07:00.0 rename3: renamed from eth1
Dec 19 11:39:14 mike-linux kernel: [    5.127193] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> (eth1): carrier is OFF
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 11:39:14 mike-linux NetworkManager[709]: <info> (eth1): preparing device
Dec 19 11:39:14 mike-linux kernel: [    8.939365] r8169 0000:04:00.0 eth1: link down
Dec 19 11:39:14 mike-linux kernel: [    8.939381] r8169 0000:04:00.0 eth1: link down
Dec 19 11:41:34 mike-linux avahi-daemon[688]: Withdrawing workstation service for eth1.
Dec 19 11:41:34 mike-linux systemd[1]: Stopping ifup for eth1...
Dec 19 11:41:34 mike-linux ifdown[2537]: /sbin/ifdown: interface eth1 not configured
Dec 19 11:41:34 mike-linux systemd[1]: Stopped ifup for eth1.
Dec 19 11:41:34 mike-linux NetworkManager[709]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Dec 19 11:41:34 mike-linux NetworkManager[709]: <info> devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:44:48 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 11:44:48 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 11:44:48 mike-linux sh[518]: Unknown interface eth1
Dec 19 11:44:48 mike-linux kernel: [    0.831646] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 11:44:48 mike-linux kernel: [    0.831772] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 11:44:48 mike-linux kernel: [    0.832030] r8169 0000:04:00.0 eth0: RTL8169sb/8110sb at 0xffffc90005b66000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 11:44:48 mike-linux kernel: [    0.832031] r8169 0000:04:00.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 11:44:48 mike-linux kernel: [    5.055868] r8168 0000:07:00.0 rename3: renamed from eth1
Dec 19 11:44:48 mike-linux kernel: [    5.083422] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> (eth1): carrier is OFF
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 11:44:49 mike-linux NetworkManager[696]: <info> (eth1): preparing device
Dec 19 11:44:49 mike-linux kernel: [    9.403406] r8169 0000:04:00.0 eth1: link down
Dec 19 11:54:13 mike-linux avahi-daemon[679]: Withdrawing workstation service for eth1.
Dec 19 11:54:13 mike-linux systemd[1]: Stopping ifup for eth1...
Dec 19 11:54:13 mike-linux ifdown[17725]: /sbin/ifdown: interface eth1 not configured
Dec 19 11:54:13 mike-linux systemd[1]: Stopped ifup for eth1.
Dec 19 11:54:13 mike-linux NetworkManager[696]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Dec 19 11:54:13 mike-linux NetworkManager[696]: <info> devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 12:03:58 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 12:03:58 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 12:03:58 mike-linux sh[537]: Unknown interface eth1
Dec 19 12:03:58 mike-linux kernel: [    5.097734] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 19 12:03:58 mike-linux kernel: [    5.097809] r8169 0000:04:00.0 (unnamed net_device) (uninitialized): not PCI Express
Dec 19 12:03:58 mike-linux kernel: [    5.098064] r8169 0000:04:00.0 eth1: RTL8169sb/8110sb at 0xffffc90005ba2000, e8:de:27:a8:9f:7d, XID 10000000 IRQ 19
Dec 19 12:03:58 mike-linux kernel: [    5.098065] r8169 0000:04:00.0 eth1: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> (eth1): carrier is OFF
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 3)
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 12:03:58 mike-linux NetworkManager[702]: <info> (eth1): preparing device
Dec 19 12:03:58 mike-linux kernel: [    9.199393] r8169 0000:04:00.0 eth1: link down
Dec 19 12:05:04 mike-linux avahi-daemon[677]: Withdrawing workstation service for eth1.
Dec 19 12:05:04 mike-linux systemd[1]: Stopping ifup for eth1...
Dec 19 12:05:04 mike-linux ifdown[2301]: /sbin/ifdown: interface eth1 not configured
Dec 19 12:05:04 mike-linux systemd[1]: Stopped ifup for eth1.
Dec 19 12:05:04 mike-linux NetworkManager[702]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Dec 19 12:05:04 mike-linux NetworkManager[702]: <info> devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 15:42:30 mike-linux systemd-modules-load[222]: Module 'r8169' is blacklisted
Dec 19 15:50:26 mike-linux kernel: [  461.389507] r8169 Gigabit Ethernet driver 6.021.00-NAPI loaded
Dec 19 15:50:26 mike-linux kernel: [  461.391202] r8169: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
Dec 19 15:50:26 mike-linux kernel: [  461.391207] eth1: RTL8169SB/8110SB at 0xffffc900060ea000, e8:de:27:a8:9f:7d, IRQ 19
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> (eth1): carrier is OFF
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 4)
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 15:50:26 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 15:50:26 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 15:50:26 mike-linux sh[15647]: Unknown interface eth1
Dec 19 15:50:26 mike-linux kernel: [  461.429134] r8169: eth1: link downDec 19 15:50:26 mike-linux NetworkManager[12353]: <info> (eth1): preparing device
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 15:50:26 mike-linux NetworkManager[12353]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net eth1, iface: eth1): no ifupdown configuration found.
Dec 19 15:56:41 mike-linux systemd-modules-load[225]: Module 'r8169' is blacklisted
Dec 19 16:38:55 mike-linux systemd-modules-load[222]: Failed to find module 'r8169'
Dec 19 16:41:23 mike-linux systemd-modules-load[216]: Failed to find module 'r8169'
Dec 19 16:46:26 mike-linux kernel: [  288.333154] r8169 Gigabit Ethernet driver 6.021.00-NAPI loaded
Dec 19 16:46:26 mike-linux kernel: [  288.334859] r8169: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
Dec 19 16:46:26 mike-linux kernel: [  288.352500] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> (eth1): carrier is OFF
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 3)
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 16:46:26 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 16:46:26 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 16:46:26 mike-linux sh[17133]: Unknown interface eth1
Dec 19 16:46:26 mike-linux kernel: [  288.377584] r8169: eth1: link downDec 19 16:46:26 mike-linux NetworkManager[689]: <info> (eth1): preparing device
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 16:46:26 mike-linux NetworkManager[689]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 16:48:07 mike-linux avahi-daemon[656]: Withdrawing workstation service for eth1.
Dec 19 16:48:07 mike-linux systemd[1]: Stopping ifup for eth1...
Dec 19 16:48:07 mike-linux ifdown[17374]: /sbin/ifdown: interface eth1 not configured
Dec 19 16:48:07 mike-linux systemd[1]: Stopped ifup for eth1.
Dec 19 16:48:07 mike-linux NetworkManager[689]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Dec 19 16:48:07 mike-linux NetworkManager[689]: <info> devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 22:23:13 mike-linux systemd-modules-load[222]: Inserted module 'r8169'
Dec 19 22:23:13 mike-linux systemd[1]: Started ifup for eth1.
Dec 19 22:23:13 mike-linux systemd[1]: Starting ifup for eth1...
Dec 19 22:23:13 mike-linux sh[529]: Unknown interface eth1
Dec 19 22:23:13 mike-linux kernel: [    4.315446] r8169 Gigabit Ethernet driver 6.021.00-NAPI loaded
Dec 19 22:23:13 mike-linux kernel: [    4.316921] r8169: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
Dec 19 22:23:13 mike-linux kernel: [    4.563905] r8169 0000:04:00.0 eth1: renamed from eth0
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1)
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> (eth1): carrier is OFF
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 19 22:23:13 mike-linux NetworkManager[697]: <info> (eth1): preparing device
Dec 19 22:23:13 mike-linux kernel: [    8.159771] r8169: eth1: link down&#9581;&#9472;mike@mike-linux ~/Downloads                                           &#9584;&#9472;&#10148;
```

---

### Post by chili555 on 2015-12-19
You have 4-5 boot sequences there so the earlier ones were before you fixed the blacklist file.

Please turn off the wireless with the switch or in Network Manager (unclick 'Enable WiFi') and then do:```
sudo ethtool -s eth1 autoneg off
```Now see if there is any change:```
dmesg | grep eth1
```If this helps, we'll make it persistent.

---

### Post by stowelly on 2015-12-20
didnt seem to have any effect apart from stopping my wifi adaptor resuming without a restart

```

&#9584;&#9472;&#10148;  dmesg | grep eth1               
[    4.578512] r8169 0000:04:00.0 eth1: renamed from eth0
[    8.215721] r8169: eth1: link down

```

Strange that ethtool shows  Link detected: no, the  cable is definitly working, have been using it in my windows partition
```

ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: no


```

---

