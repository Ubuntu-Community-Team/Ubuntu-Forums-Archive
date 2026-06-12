---
title: "Bluetooth not responding on Ubuntu 22.04"
date: 2023-05-07
forum: Networking &amp; Wireless
---

### Post by thomas92600 on 2023-05-07
Hello,

I have just got an Acer Swift SFA16, and I directly installed Ubuntu 22.04, after temporarily disabling the secure boot mode. 
It appears that Bluetooth seems to be active, but it is not responding in the settings interface

here are some command output:

```

$ sudo systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2023-05-07 15:04:38 CEST; 11min ago
       Docs: man:bluetoothd(8)
   Main PID: 638 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18116)
     Memory: 1.8M
        CPU: 43ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;638 /usr/lib/bluetooth/bluetoothd
```

```
inxi -E
Bluetooth:
  Device-1: Foxconn / Hon Hai Wireless_Device type: USB driver: btusb
  Report: hciconfig ID: hci0 rfk-id: 1 state: down
    bt-service: enabled,running rfk-block: hardware: no software: no
    address: 00:00:00:00:00:00
```
```

~$ bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
[bluetooth]# 
```

It appears that there are no proprietary drivers to be installed in "Software&Updates"

I guess it is a matter of driver, I find a lot of post on internet that suggest that, but I fear that they are outdated.
They don't solve my issue anyway,

Any Idea?

Than you for your help,

Thomas

---

### Post by jeremy31 on 2023-05-07
Please post results from terminal for ```
lsusb; dmesg | egrep -i 'blue|firm'; hciconfig -a
```

---

### Post by thomas92600 on 2023-05-07
Thank you very much for your help!

Here it is:

```
$ lsusb; dmesg | egrep -i 'blue|firm'; hciconfig -a
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0408:4036 Quanta Computer, Inc. Acer FHD User Facing
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0489:e0e4 Foxconn / Hon Hai Wireless_Device
Bus 003 Device 002: ID 093a:2533 Pixart Imaging, Inc. Gaming Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04f3:0c7f Elan Microelectronics Corp. ELAN:Fingerprint
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dmesg: read kernel buffer failed: Operation not permitted
hci0:    Type: Primary  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:6 acl:0 sco:0 commands:2 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: PERIPHERAL ACCEPT 
```

---

### Post by jeremy31 on 2023-05-07
Results for ```
sudo dmesg | egrep -i 'blue|firm'; uname -r; mokutil --sb
```

---

### Post by thomas92600 on 2023-05-07
```
[    0.096432] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.280030] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.301103] [Firmware Info]: PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] not reserved in ACPI motherboard resources
[    2.165763] Bluetooth: Core ver 2.22
[    2.165790] NET: Registered PF_BLUETOOTH protocol family
[    2.165792] Bluetooth: HCI device and connection manager initialized
[    2.165796] Bluetooth: HCI socket layer initialized
[    2.165798] Bluetooth: L2CAP socket layer initialized
[    2.165803] Bluetooth: SCO socket layer initialized
[    2.574448] mt7921e 0000:02:00.0: WM Firmware Version: ____000000, Build Time: 20221227123243
[    3.148132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.148137] Bluetooth: BNEP filters: protocol multicast
[    3.148142] Bluetooth: BNEP socket layer initialized
[    3.157502] [drm] Loading DMUB firmware via PSP: version=0x04000022
[    3.160601] [drm] Found VCN firmware Version ENC: 1.21 DEC: 2 VEP: 0 Revision: 10
[    3.160607] amdgpu 0000:61:00.0: amdgpu: Will use PSP to load VCN firmware
[    4.296473] Bluetooth: hci0: Opcode 0x c03 failed: -110
[  754.186017] Bluetooth: hci0: Opcode 0x c03 failed: -110
[ 2470.061623] Modules linked in: cmac ccm intel_rapl_msr intel_rapl_common bnep snd_soc_acp6x_mach snd_soc_dmic snd_acp6x_pdm_dma snd_sof_amd_renoir snd_sof_amd_acp snd_sof_pci snd_sof snd_sof_utils snd_soc_core edac_mce_amd mt7921e amdgpu snd_compress snd_hda_codec_realtek mt7921_common ac97_bus kvm_amd snd_hda_codec_generic snd_pcm_dmaengine mt76_connac_lib iommu_v2 ledtrig_audio snd_hda_codec_hdmi snd_pci_ps kvm snd_hda_intel snd_intel_dspcfg btusb snd_intel_sdw_acpi uvcvideo btrtl gpu_sched btbcm drm_ttm_helper snd_acp_pci snd_seq_midi crct10dif_pclmul mt76 videobuf2_vmalloc snd_hda_codec btintel ghash_clmulni_intel snd_seq_midi_event ttm videobuf2_memops binfmt_misc btmtk aesni_intel snd_pci_acp6x drm_display_helper mac80211 snd_hda_core snd_rawmidi videobuf2_v4l2 crypto_simd bluetooth input_leds videobuf2_common snd_hwdep snd_pci_acp5x cryptd cec snd_rn_pci_acp3x videodev snd_seq rc_core acer_wmi snd_acp_config ecdh_generic rapl serio_raw nls_iso8859_1 hid_multitouch wmi_bmof
5.19.0-41-generic
SecureBoot disabled
```

---

### Post by jeremy31 on 2023-05-07
Try ```
sudo apt install git dkms
git clone https://github.com/jeremyb31/bluetooth-5.19.git
sudo dkms add ./bluetooth-5.19
sudo dkms install btusb/4.0
```
Reboot

---

### Post by thomas92600 on 2023-05-12
Hello,
Actually, I realized that the Bluetooth of my PC is not compatible yet with Ubuntu
I solve the problem with a Bluetooth dongle
Thank you again for your suggestions!

---

### Post by jeremy31 on 2023-05-13
The code I posted should have made that bluetooth compatible

---

### Post by bjblevins on 2023-07-03
Thank you!  This fixed my bluetooth mouse (can't connect) on Xubuntu 23.04.

---

