---
title: "Bluetooth  icon  missing on the top bar"
date: 2024-04-05
forum: Networking &amp; Wireless
---

### Post by Freiklite on 2024-04-05
Hi,
    I use Mantic Minautor on a 14s-fq hp laptop.
    My Q.live 1242 wireless earphones are not detected.
    No bluetooth icon in the right topbar.

    A few details:
```
$ uname -a; lspci -nnk | grep -iA3 net; lsusb; sudo dmesg | grep -i bluetooth; sudo dmesg | grep -i firmware; lsmod | grep bluetooth
Linux tinnitus-HP-Laptop-14s-fq0xxx 6.5.0-26-generic #26-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar  5 21:19:28 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    DeviceName: Realtek Wireless LAN + BT
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
    Kernel driver in use: rtw_8821ce
    Kernel modules: rtw88_8821ce
02:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller 980 [144d:a809]
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. Realtek Bluetooth 4.2 Adapter
Bus 001 Device 003: ID 0408:5365 Quanta Computer, Inc. HP TrueVision HD Camera
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[sudo] Mot de passe de tinnitus : 
[ 3348.100607] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 3349.992567] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 3351.976447] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 4340.964598] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 4342.948586] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
bluetooth            1077248  44 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth
```

```
$ dpkg -l | grep blue
ii  bluez                                          5.68-0ubuntu1.1                         amd64        Bluetooth tools and daemons
ii  bluez-alsa-utils                               4.0.0-2                                 amd64        Bluetooth Audio ALSA Backend (utils)
ii  bluez-btsco                                    1:0.50-0ubuntu7                         amd64        Bluez Bluetooth SCO tool
ii  bluez-cups                                     5.68-0ubuntu1.1                         amd64        Bluetooth printer driver for CUPS
ii  bluez-firmware                                 1.2-9                                   all          Firmware for Bluetooth devices
ii  bluez-hcidump                                  5.68-0ubuntu1.1                         amd64        Analyses Bluetooth HCI packets
ii  bluez-meshd                                    5.68-0ubuntu1.1                         amd64        bluetooth mesh daemon
ii  bluez-obexd                                    5.68-0ubuntu1.1                         amd64        bluez obex daemon
ii  bluez-tests                                    5.68-0ubuntu1.1                         amd64        BlueZ test tools and scripts
ii  bluez-tools                                    2.0~20170911.0.7cb788c-4                amd64        Set of tools to manage Bluetooth devices for linux
ii  gir1.2-gnomebluetooth-3.0:amd64                42.6-1                                  amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth-3-common                       42.6-1                                  all          GNOME Bluetooth 3 common files
ii  libasound2-plugin-bluez:amd64                  4.0.0-2                                 amd64        Bluetooth Audio ALSA Backend (plugins)
ii  libbluetooth3:amd64                            5.68-0ubuntu1.1                         amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth-3.0-13:amd64                42.6-1                                  amd64        GNOME Bluetooth 3 support library
ii  libgnome-bluetooth-ui-3.0-13:amd64             42.6-1                                  amd64        GNOME Bluetooth 3 UI support library
ii  libspa-0.2-bluetooth:amd64                     0.3.79-2                                amd64        libraries for the PipeWire multimedia server - bluetooth plugins


```

```
$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
 $ sudo service bluetooth status | cat
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; preset: enabled)
     Active: active (running) since Thu 2024-04-04 21:45:57 CEST; 1h 18min ago
       Docs: man:bluetoothd(8)
   Main PID: 815 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 8670)
     Memory: 2.3M
        CPU: 243ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;815 /usr/lib/bluetooth/bluetoothd

avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_1
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_0
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_1
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_0
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/faststream
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/faststream_duplex
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSink/opus_05
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/opus_05
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSink/opus_05_duplex
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/opus_05_duplex
```

Thank you for your attention and suggestions,
Ciao

---

### Post by jeremy31 on 2024-04-05
In terminal check ```
mokutil --sb
```
Secure Boot will need to be disabled for it to work, then
```
sudo apt install git dkms
git clone https://github.com/jeremyb31/bluetooth-6.5.git
sudo dkms add ./bluetooth-6.5
sudo dkms install btusb/4.1
```
Reboot

---

### Post by Freiklite on 2024-04-05
Hi,
Thank you very much for your answer.

I made the changes.

There is*n't any icon in top bar.*
*My earphone* devices cannot be connected.

Before the changes I noticed that launching the device search froze Freetuxtv.

Ciao

---

### Post by jeremy31 on 2024-04-05
Post results for ```
modinfo btusb; sudo dmesg|egrep -i 'blue|firm'
```

---

### Post by Freiklite on 2024-04-06
Hi,
here's the answer:
```
:~$ modinfo btusb; sudo dmesg|egrep -i 'blue|firm'
filename:       /lib/modules/6.5.0-26-generic/updates/dkms/btusb.ko.zst
license:        GPL
version:        0.91
description:    Generic Bluetooth USB driver ver 0.91
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     D9883A412AC657D8A99A40A
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v413Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0BB4p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v105Bp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp04ic*isc*ip*in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
alias:          of:N*T*Cusb4ca,301aC*
alias:          of:N*T*Cusb4ca,301a
alias:          of:N*T*Cusbcf3,e300C*
alias:          of:N*T*Cusbcf3,e300
alias:          of:N*T*Cusb1286,204eC*
alias:          of:N*T*Cusb1286,204e
depends:        bluetooth,btmtk,btrtl,btintel,btbcm
retpoline:      Y
name:           btusb
vermagic:       6.5.0-26-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         tinnitus-HP-Laptop-14s-fq0xxx Secure Boot Module Signature key
sig_key:        40:45:85:7B:6C:C4:ED:8F:26:19:77:99:2E:FC:90:28:3E:AE:53:29
sig_hashalgo:   sha512
signature:      BE:20:71:4A:6B:36:AF:1A:15:71:92:55:B8:2F:CB:70:4D:14:AB:00:
        D6:69:92:A3:10:09:92:5F:CA:B3:B2:59:66:B2:14:93:34:A5:09:DA:
        C6:86:59:3E:90:5C:E2:A0:6C:F1:C3:38:FF:F1:CD:67:31:D0:85:C8:
        19:E2:2F:54:9B:A4:A3:70:99:94:2E:19:75:C5:0B:9F:68:CC:E2:A7:
        F2:33:C0:BC:C6:CB:8F:E2:D5:8E:90:3F:3F:D1:D3:D8:B9:3B:05:6B:
        0E:70:D7:3C:62:F7:F6:B6:A1:71:54:FE:6C:5A:84:30:06:20:F9:02:
        E3:06:65:74:28:82:88:61:4A:A4:65:1B:69:9C:C6:41:B2:8B:F0:44:
        73:4D:6E:B9:FF:FF:3F:38:CA:C3:FF:4B:9D:F4:67:B7:D7:4E:A1:57:
        F5:C4:79:01:21:6C:F7:9E:51:3A:32:D7:44:E7:C4:1A:98:E5:AC:B3:
        26:72:11:95:99:EC:6A:96:22:B9:CD:5B:51:4D:6D:A5:4D:96:1F:9C:
        3F:72:8C:39:93:87:10:C0:F8:FE:07:26:D4:02:03:E6:09:57:8C:60:
        E7:4E:FC:FB:7B:D0:00:5E:77:AF:4A:BA:DC:73:07:E1:71:30:14:AB:
        8C:A2:17:29:6A:A0:FF:14:BA:62:DD:69:98:CF:82:A0
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           enable_autosuspend:Enable USB autosuspend by default (bool)
parm:           reset:Send HCI reset command on initialization (bool)
[sudo] Mot de passe de tinnitus : 
Désolé, essayez de nouveau.
[sudo] Mot de passe de tinnitus : 
[    0.082860] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.244879] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.214433] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    2.286728] wmi_bus wmi_bus-PNP0C14:00: [Firmware Info]: 8F1F6436-9F42-42C8-BADC-0E9424F20C9A has zero instances
[    2.286735] wmi_bus wmi_bus-PNP0C14:00: [Firmware Info]: 8F1F6435-9F42-42C8-BADC-0E9424F20C9A has zero instances
[    2.286737] wmi_bus wmi_bus-PNP0C14:00: [Firmware Info]: 7391A661-223A-47DB-A77A-7BE84C60822D has zero instances
[    2.286739] wmi_bus wmi_bus-PNP0C14:00: [Firmware Info]: DF4E63B6-3BBC-4858-9737-C74F82F821F3 has zero instances
[    3.580390] usb 1-4: Product: Bluetooth Radio 
[    5.005821] systemd[1]: systemd-pcrmachine.service - TPM2 PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/StubPcrKernelImage-4a67b082-0a4c-41cf-b6c7-440b29bb8c4f).
[    5.720287] Bluetooth: Core ver 2.22
[    5.720459] NET: Registered PF_BLUETOOTH protocol family
[    5.720462] Bluetooth: HCI device and connection manager initialized
[    5.720502] Bluetooth: HCI socket layer initialized
[    5.720506] Bluetooth: L2CAP socket layer initialized
[    5.720512] Bluetooth: SCO socket layer initialized
[    5.767121] Bluetooth: hci0: RTL: examining hci_ver=08 hci_rev=000c lmp_ver=08 lmp_subver=8821
[    5.769146] Bluetooth: hci0: RTL: rom_version status=0 version=1
[    5.769159] Bluetooth: hci0: RTL: loading rtl_bt/rtl8821c_fw.bin
[    5.770544] Bluetooth: hci0: RTL: loading rtl_bt/rtl8821c_config.bin
[    5.771105] Bluetooth: hci0: RTL: cfg_sz 10, total sz 34926
[    5.820151] rtw_8821ce 0000:01:00.0: Firmware version 24.11.0, H2C version 12
[    6.378166] Bluetooth: hci0: RTL: fw version 0x75b8f098
[    9.821351] [drm] Loading DMUB firmware via PSP: version=0x01010027
[    9.822456] [drm] Found VCN firmware Version ENC: 1.20 DEC: 6 VEP: 0 Revision: 0
[    9.822472] amdgpu 0000:03:00.0: amdgpu: Will use PSP to load VCN firmware
[   10.435930] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.435939] Bluetooth: BNEP filters: protocol multicast
[   10.435945] Bluetooth: BNEP socket layer initialized
[   10.445381] Bluetooth: MGMT ver 1.22
[   12.517804] Bluetooth: RFCOMM TTY layer initialized
[   12.517819] Bluetooth: RFCOMM socket layer initialized
[   12.517827] Bluetooth: RFCOMM ver 1.11
[   85.362071] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  168.988408] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  232.267832] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  253.055942] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  277.884424] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  322.471729] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  339.842950] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  354.435057] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  393.545692] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  448.513463] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  454.866864] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt
[  469.412773] rtw_8821ce 0000:01:00.0: unhandled firmware c2h interrupt

```
Ciao

---

### Post by Freiklite on 2024-04-06
Hi,
 After a new try everything is ok, icon, device list and sound.
Thank you very much,
D.B.

---

