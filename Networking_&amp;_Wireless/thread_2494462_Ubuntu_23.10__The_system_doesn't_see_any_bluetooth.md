---
title: "Ubuntu 23.10 | The system doesn't see any bluetooth devices"
date: 2024-01-17
forum: Networking &amp; Wireless
---

### Post by jsn33 on 2024-01-17
I was listening to a music and suddenly my wireless connection with AirPods had lost. Then I tried to reconnect and moreover reboot, but it hasn't helped at all. My system cannot find any devices. Here is some useful information:
```
$ sudo dmesg | grep -i 'blue'
[    1.597997] usb 3-2: Product: Bluetooth Radio
[    2.079343] Bluetooth: Core ver 2.22
[    2.079373] NET: Registered PF_BLUETOOTH protocol family
[    2.079376] Bluetooth: HCI device and connection manager initialized
[    2.079382] Bluetooth: HCI socket layer initialized
[    2.079385] Bluetooth: L2CAP socket layer initialized
[    2.079390] Bluetooth: SCO socket layer initialized
[    2.170585] Bluetooth: hci0: RTL: examining hci_ver=0c hci_rev=dbc6 lmp_ver=0c lmp_subver=b20f
[    2.383624] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000b lmp_ver=0b lmp_subver=8852
[    2.385575] Bluetooth: hci0: RTL: rom_version status=0 version=1
[    2.385586] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852bu_fw.bin
[    2.386591] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852bu_config.bin
[    2.386726] Bluetooth: hci0: RTL: cfg_sz 6, total sz 58003
[    2.944977] Bluetooth: hci0: RTL: fw version 0xdbc6b20f
[    3.108594] Bluetooth: hci0: AOSP extensions version v1.00
[    3.108601] Bluetooth: hci0: AOSP quality report is supported
[    4.768453] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.768463] Bluetooth: BNEP filters: protocol multicast
[    4.768470] Bluetooth: BNEP socket layer initialized
[    4.770442] Bluetooth: MGMT ver 1.22
[    6.255229] Bluetooth: RFCOMM TTY layer initialized
[    6.255238] Bluetooth: RFCOMM socket layer initialized
[    6.255244] Bluetooth: RFCOMM ver 1.11
[    6.793331] audit: type=1400 audit(1705506663.802:137): apparmor="DENIED" operation="connect" class="file" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=988 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    6.798016] audit: type=1400 audit(1705506663.806:138): apparmor="DENIED" operation="create" class="net" profile="snap.bluez.bluez" pid=979 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[    6.813323] audit: type=1400 audit(1705506663.822:139): apparmor="DENIED" operation="connect" class="file" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=979 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    7.016405] audit: type=1400 audit(1705506664.026:140): apparmor="DENIED" operation="create" class="net" profile="snap.bluez.bluez" pid=1497 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[    7.016586] audit: type=1400 audit(1705506664.026:141): apparmor="DENIED" operation="connect" class="file" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1497 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    7.020421] audit: type=1400 audit(1705506664.030:142): apparmor="DENIED" operation="connect" class="file" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1498 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[    7.284807] audit: type=1400 audit(1705506664.294:143): apparmor="DENIED" operation="create" class="net" profile="snap.bluez.bluez" pid=1591 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
```

---

### Post by rectec794613 on 2024-01-22
Looks like [AppArmor]("https://wiki.ubuntu.com/AppArmor") is being overprotective and interfering with Bluetooth. Something may have modified your security profiles.

In /etc/apparmor.d/, do you see any files along the lines of *snap.bluez.** or *usr.lib.bluetooth.bluetoothd*?

Try this, I think it should reset your AppArmor profiles:
```
sudo apt-get install --reinstall apparmor-profiles
```
And then reboot.

If you haven't already, it couldn't hurt to install updates.

---

### Post by beehead180 on 2024-01-27
I just installed Ubuntu 23.10 on HP fc0-xxx Laptop.  I was forced to install using SAFE GRAFIC INSTALL.

---

