---
title: "Yet Another Issue With Bluetooth"
date: 2020-04-23
forum: Networking &amp; Wireless
---

### Post by cobras on 2020-04-23
Hey Flolks,

I've searched this and other forums but I cannot get my bluetooth to work for me.  I'm running Ubuntu 18.04 on a Toshiba Satellite C55-A.  I've tried uninstalling and reinstalling, starting, restarting and other things I only somewhat understood but can't get it to work.

Here's what I get in my terminal

me:~$ systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
Condition: start condition failed at Thu 2020-04-23 16:56:17 PDT; 32min ago
           &#9492;&#9472; ConditionPathIsDirectory=/sys/class/bluetooth was not met
     Docs: man:bluetoothd(8)
lines 1-6/6 (END)

As you can see something is running in the background, but I don't know what.

Any ideas?

---

### Post by wildmanne39 on 2020-04-23
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by jeremy31 on 2020-04-24
Post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by cobras on 2020-04-24
me:~$ lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
01:00.0 Ether[COLOR=#EF2929]**net**[/COLOR] controller [0200]: Qualcomm Atheros AR8162 Fast Ether[COLOR=#EF2929]**net**[/COLOR] [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems AR8162 Fast Ether[COLOR=#EF2929]**net**[/COLOR] [1179:ff1e]
    Kernel driver in use: alx
    Kernel modules: alx
02:00.0 [COLOR=#EF2929]**Net**[/COLOR]work controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless [COLOR=#EF2929]**Net**[/COLOR]work Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless [COLOR=#EF2929]**Net**[/COLOR]work Adapter [10ec:0191]
    Kernel driver in use: rtl8188ee
    Kernel modules: rtl8188ee
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:e374 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.030755] Spectre V2 : Enabling Restricted Speculation for [COLOR=#EF2929]**firm**[/COLOR]ware calls
[   34.640756] rtl8188ee: Using [COLOR=#EF2929]**firm**[/COLOR]ware rtlwifi/rtl8188efw.bin
[   58.312552] audit: type=1400 audit(1587736899.832:60): apparmor="DENIED" operation="create" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" pid=1253 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" family="[COLOR=#EF2929]**blue**[/COLOR]tooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   58.353052] audit: type=1400 audit(1587736899.872:61): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.obex" name="/run/dbus/system_bus_socket" pid=1250 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   58.411679] audit: type=1400 audit(1587736899.928:62): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" name="/run/dbus/system_bus_socket" pid=1253 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   58.621272] audit: type=1400 audit(1587736900.140:63): apparmor="DENIED" operation="create" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" pid=1368 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" family="[COLOR=#EF2929]**blue**[/COLOR]tooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   58.621463] audit: type=1400 audit(1587736900.140:64): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.obex" name="/run/dbus/system_bus_socket" pid=1369 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   58.621467] audit: type=1400 audit(1587736900.140:65): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" name="/run/dbus/system_bus_socket" pid=1368 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   58.868747] audit: type=1400 audit(1587736900.388:66): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.obex" name="/run/dbus/system_bus_socket" pid=1422 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   58.871250] audit: type=1400 audit(1587736900.388:67): apparmor="DENIED" operation="create" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" pid=1423 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" family="[COLOR=#EF2929]**blue**[/COLOR]tooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   58.871512] audit: type=1400 audit(1587736900.388:68): apparmor="DENIED" operation="connect" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" name="/run/dbus/system_bus_socket" pid=1423 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   59.124450] audit: type=1400 audit(1587736900.644:69): apparmor="DENIED" operation="create" profile="snap.[COLOR=#EF2929]**blue**[/COLOR]z.[COLOR=#EF2929]**blue**[/COLOR]z" pid=1475 comm="[COLOR=#EF2929]**blue**[/COLOR]toothd" family="[COLOR=#EF2929]**blue**[/COLOR]tooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
me:~$

---

### Post by jeremy31 on 2020-04-25
I don't see any sign of bluetooth hardware installed

---

### Post by cobras on 2020-04-25
So I need a dongle.  I'm glad I asked before I did something really stupid.

Thank you.

---

