---
title: "Bluetooth : No device found (rtl8822cu firmware)"
date: 2020-11-24
forum: Networking &amp; Wireless
---

### Post by Olivier V on 2020-11-24
Hi,

I use kubuntu 20.04 and the Bluetooteh doesn't work
When I go to System Configuration -> Bluetooth, I have the message "**No Bluetooth found. Plug in a dongle to use Bluetooth.**"

The computer is Asus TUF 17 and I wrote this page about this computer : [https://doc.ubuntu-fr.org/asus-a17-tuf766iu](https://doc.ubuntu-fr.org/asus-a17-tuf766iu)
Bluetooth is internal on the motherboard.

It tries to use rtl8822cu firmware.

I use 5.9.10 kernel to support AMD Ryzen 7.

Thank you for help.

```

meloli@Asus-A17:~$ sudo dmesg | grep -i bluetooth                  
[    1.476073] usb 5-1: Product: Bluetooth Radio
[    3.977975] Bluetooth: Core ver 2.22
[    3.978022] Bluetooth: HCI device and connection manager initialized
[    3.978030] Bluetooth: HCI socket layer initialized
[    3.978035] Bluetooth: L2CAP socket layer initialized
[    3.978043] Bluetooth: SCO socket layer initialized
[    4.002039] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000c lmp_ver=0a lmp_subver=8822
[    4.003996] Bluetooth: hci0: RTL: rom_version status=0 version=3
[    4.004001] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822cu_fw.bin
[    4.006885] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822cu_config.bin
[    4.007705] Bluetooth: hci0: RTL: cfg_sz 6, total sz 31422
[    4.283989] Bluetooth: hci0: RTL: fw version 0x09993aa1
[    4.933204] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.933207] Bluetooth: BNEP filters: protocol multicast
[    4.933214] Bluetooth: BNEP socket layer initialized
[ 1422.650815] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000c lmp_ver=0a lmp_subver=8822
[ 1422.652695] Bluetooth: hci0: RTL: rom_version status=0 version=3
[ 1422.652725] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822cu_fw.bin
[ 1422.652877] Bluetooth: hci0: RTL: loading rtl_bt/rtl8822cu_config.bin
[ 1422.653058] Bluetooth: hci0: RTL: cfg_sz 6, total sz 31422
[ 1422.931399] Bluetooth: hci0: RTL: fw version 0x09993aa1
[ 1632.862056] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=0999 lmp_ver=0a lmp_subver=3aa1
[ 1632.862064] Bluetooth: hci0: RTL: unknown IC info, lmp subver 3aa1, hci rev 0999, hci ver 000a
[ 1632.862065] Bluetooth: hci0: RTL: assuming no firmware upload needed
meloli@Asus-A17:~$ lsmod|grep blue
bluetooth             647168  12 btrtl,btintel,btbcm,bnep,btusb
ecdh_generic           16384  1 bluetooth

```

```
meloli@Asus-A17:~$ lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 13d3:3548 IMC Networks Bluetooth Radio
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13d3:56a2 IMC Networks USB2.0 HD UVC WebCam
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

meloli@Asus-A17:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

---

### Post by Raffles727 on 2020-11-24
Did you disable secure boot in UEFI/BIOS before installing kubuntu?

---

### Post by jeremy31 on 2020-11-24
That might need a kernel patch to fix, [https://marc.info/?l=linux-bluetooth&m=160378222632366&w=2](https://marc.info/?l=linux-bluetooth&m=160378222632366&w=2)
This patch hasn't been accepted to the upstream Linus kernel yet

---

### Post by Olivier V on 2020-11-25
Secure boot is disabled.

I don't understand how to use the patch.

It should work with kernel >5.7 : [https://linux-hardware.org/index.php?id=usb:13d3-3548&page=1#status](https://linux-hardware.org/index.php?id=usb:13d3-3548&page=1#status)
I sue the latest 5.9.10 kernel.

---

### Post by jeremy31 on 2020-11-25
But something about your BT chip is different, do a search for "unknown IC info, lmp subver 3aa1, hci rev 0999, hci ver 000a"

Some of the chipsets with the same USB ID do not have this problem and the reference to the 5.7 kernel likely means that is when the USB ID was added to btusb.c in the source code

---

### Post by Olivier V on 2020-11-27
I found this [https://bbs.archlinux.org/viewtopic.php?id=259975&p=3](https://bbs.archlinux.org/viewtopic.php?id=259975&p=3) marked as solved, but I don't understand what I should do...

EDIT1 : I tried with mainline 5.8.0 kernel and with this kernel Bluetooths works.

EDIT2 : As said here [https://bbs.archlinux.org/viewtopic.php?pid=1940003#p1940003](https://bbs.archlinux.org/viewtopic.php?pid=1940003#p1940003), it should perhaps be solved in 5.9.11 kernel ?

---

### Post by Olivier V on 2020-12-02
I open bug report :

[https://bugzilla.kernel.org/show_bug.cgi?id=210453](https://bugzilla.kernel.org/show_bug.cgi?id=210453)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906515](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906515)

---

### Post by Olivier V on 2020-12-18
As asked here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906515](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906515) I've done a git bisect.

Here is the answer

```
meloli@Asus-A17:~/Bureau/meloli/GITBISECT/linux$ git bisect bad
b2cc23398e8166b38f8715026273503b081c2a7a is the first bad commit
commit b2cc23398e8166b38f8715026273503b081c2a7a
Author: Sathish Narasimman <nsathish41@gmail.com>
Date:   Thu Jul 23 18:09:02 2020 +0530

    Bluetooth: Enable RPA Timeout
    
    Enable RPA timeout during bluetooth initialization.
    The RPA timeout value is used from hdev, which initialized from
    debug_fs
    
    Signed-off-by: Sathish Narasimman <sathish.narasimman@intel.com>
    Signed-off-by: Marcel Holtmann <marcel@holtmann.org>

 include/net/bluetooth/hci.h | 2 ++
 net/bluetooth/hci_core.c    | 8 ++++++++
 2 files changed, 10 insertions(+)
```

---

