---
title: "Troubleshooting Bluetooth Pairing Issues with Logitech Devices on HP Victus Gaming"
date: 2024-01-26
forum: Networking &amp; Wireless
---

### Post by ransho on 2024-01-26
Hello everyone,
This is my first post and I'm new here - hope I do it in the right format.


I have a Logitech keyboard and mouse (MX keys & MX master 3s)
I moved from an old computer (HP Laptop 15-dw3xxx with ubuntu 22.04) where the Bluetooth pairing of the keyboard and mouse works without a problem,
For a new computer (HP Victus Gaming Laptop 16-r0008nj (800K3EA))
First I installed the same operating system on it (ubuntu 22.04) but I couldn't find the devices in the Bluetooth list, so I upgraded to Ubuntu 23.10
I can't pair the keyboard and the mouse no matter what I do!
please help?
Thank you all :)


maybe thats help
```


ran@ran-Type1ProductConfigId:~$ inxi -Fzx


System:
  Kernel: 6.5.0-14-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 45.2 Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 16-r0xxx
    v: Type1ProductConfigId serial: <superuser required>
  Mobo: HP model: 8BBE v: 77.35 serial: <superuser required> UEFI: Insyde
    v: F.12 date: 10/27/2023
Battery:
  ID-1: BAT1 charge: 69.2 Wh (100.0%) condition: 69.2/70.1 Wh (98.7%)
    volts: 17.4 min: 15.4 model: 333-AC-4B-A WK04070XL status: full
CPU:
  Info: 14-core (6-mt/8-st) model: 13th Gen Intel Core i7-13700H bits: 64
    type: MST AMCP arch: Raptor Lake rev: 2 cache: L1: 1.2 MiB L2: 11.5 MiB
    L3: 24 MiB
  Speed (MHz): avg: 415 high: 570 min/max: 400/4800:5000:3700 cores: 1: 400
    2: 400 3: 400 4: 400 5: 548 6: 400 7: 570 8: 400 9: 400 10: 400 11: 400
    12: 400 13: 400 14: 400 15: 400 16: 400 17: 400 18: 400 19: 400 20: 400
    bogomips: 116736
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Raptor Lake-P [Iris Xe Graphics] vendor: Hewlett-Packard
    driver: i915 v: kernel arch: Gen-13 bus-ID: 00:02.0
  Device-2: NVIDIA AD106M [GeForce RTX 4070 Max-Q / Mobile]
    vendor: Hewlett-Packard GN21-X6 driver: nvidia v: 535.154.05 arch: Lovelace
    bus-ID: 01:00.0
  Device-3: Luxvisions Innotech HP True Vision FHD Camera driver: uvcvideo
    type: USB bus-ID: 3-7:3
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa dri: iris gpu: i915
    resolution: 2560x1440~240Hz
  API: OpenGL v: 4.6 Mesa 23.2.1-1ubuntu3.1 renderer: Mesa Intel Graphics
    (RPL-P) direct-render: Yes
Audio:
  Device-1: Intel Raptor Lake-P/U/H cAVS vendor: Hewlett-Packard
    driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  API: ALSA v: k6.5.0-14-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 03:00.0
  IF: eno1 state: down mac: <filter>
  Device-2: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 04:00.0
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device driver: btusb v: 0.8 type: USB
    bus-ID: 3-10:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.2
    lmp-v: 11
Drives:
  Local Storage: total: 953.87 GiB used: 16.63 GiB (1.7%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL21T0HCLR-00BH1
    size: 953.87 GiB temp: 28.9 C
Partition:
  ID-1: / size: 936.79 GiB used: 16.62 GiB (1.8%) fs: ext4 dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 8 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: N/A mobo: N/A
  Fan Speeds (rpm): cpu: 0 fan-2: 0
Info:
  Processes: 360 Uptime: 17m Memory: total: 32 GiB note: est.
  available: 31.03 GiB used: 1.77 GiB (5.7%) Init: systemd
  target: graphical (5) Compilers: N/A Packages: 1865 Shell: Bash v: 5.2.15
  inxi: 3.3.29

```

**updating**
Adds hciconfig -a from both computers
There is a difference in Manufacturer

HP-Laptop-15-dw3xxx
```

ran@ran-HP-Laptop-15-dw3xxx:~$ hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 68:3E:26:40:E2:AE  ACL MTU: 1021:4  SCO MTU: 96:6
    UP RUNNING PSCAN ISCAN
    RX bytes:70363729 acl:1368492 sco:0 events:1038650 errors:0
    TX bytes:111842008 acl:170989 sco:0 commands:4696 errors:0
    Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
    Link policy: RSWITCH SNIFF
    Link mode: PERIPHERAL ACCEPT
    Name: 'ran-HP-Laptop-15-dw3xxx'
    Class: 0x7c010c
    Service Classes: Rendering, Capturing, Object Transfer, Audio, Telephony
    Device Class: Computer, Laptop
    HCI Version: 5.2 (0xb)  Revision: 0x20ce
    LMP Version: 5.2 (0xb)  Subversion: 0x20ce
    Manufacturer: Intel Corp. (2)



```


HP Victus Gaming Laptop 16-r0008nj (800K3EA)
```

ran@ran-Type1ProductConfigId:~$ hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 10:68:38:3D:8C:68  ACL MTU: 1021:6  SCO MTU: 240:8
    UP RUNNING
    RX bytes:9224 acl:0 sco:0 events:400 errors:0
    TX bytes:5440 acl:0 sco:0 commands:381 errors:0
    Features: 0xbf 0x3e 0x8d 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
    Link policy: RSWITCH SNIFF
    Link mode: PERIPHERAL ACCEPT
    Name: 'ran-Type1ProductConfigId'
    Class: 0x7c010c
    Service Classes: Rendering, Capturing, Object Transfer, Audio, Telephony
    Device Class: Computer, Laptop
    HCI Version: 5.2 (0xb)  Revision: 0x2918
    LMP Version: 5.2 (0xb)  Subversion: 0x2303
    Manufacturer: MediaTek, Inc. (70)




```

---

### Post by jeremy31 on 2024-01-26
Post results from the Victus in terminal for ```
lsusb
```

---

### Post by ransho on 2024-01-26
```

ran@ran-Type1ProductConfigId:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 30c9:009f Luxvisions Innotech Limited HP True Vision FHD Camera
Bus 003 Device 004: ID 13d3:3567 IMC Networks Wireless_Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jeremy31 on 2024-01-26
Secure Boot must be disabled then in terminal ```
sudo apt install git dkms 
git clone https://github.com/jeremyb31/bluetooth-6.5.git
sudo dkms add ./bluetooth-6.5
sudo dkms install btusb/4.1
```
Reboot

---

### Post by ransho on 2024-01-26
First of all - thanks for the help!


I did the steps, still I don't see the keyboard and mouse.
Note that I see other devices in the list


I am attaching a picture from the new computer (gaming),

and the old one (where you see the keyboard and mouse)

---

### Post by ransho on 2024-01-26
the new pc BT list

---

### Post by VMC on 2024-01-26
Here's some bluetooth trouble shooting help:
[https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho](https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho)

---

### Post by ransho on 2024-01-26
I appreciate your willingness to assist :)


However, the issue I'm encountering isn't with the Bluetooth connectivity&#8212;it's operational and detects devices. 
The challenge lies in the fact that it fails to identify the keyboard and mouse.

---

### Post by jeremy31 on 2024-01-26
Are the mouse and keyboard in pairing mode when you are searching for them?  I know some devices can only be paired to one device at a time

---

### Post by ransho on 2024-01-27
Of course they are in pairing mode,
This Logitech keyboard and mouse support simultaneous connection to 3 different devices each.

---

### Post by ransho on 2024-01-30
Maybe I'll focus the problem.
I manage to connect bluetooth devices (for example headphones)
Only the Logitech devices I don't see in the list.
Thanks :)

---

