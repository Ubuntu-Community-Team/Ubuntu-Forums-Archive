---
title: "Cannot make Bluetooth discoverable"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by Agnishom_Chattopadhyay on 2018-08-30
Hi;

I am dual booting Windows 10 with Ubuntu 18 and I cannot seem to use my Bluetooth. The GUI Bluetooth manager given by the OS detects that there is a bluetooth, but cannot discover any other device. Neither can I detect my device from any other device.

Any help is appreciated. I have added the output of some relevant commands.


```
amitb@amit-PC:/media/amitb/Ubuntu 18.04 LTS amd64$ lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:81db]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [%2F&h=AT20D9y7EoQAVVZbLept7KMDerWbvcD48gM9O5ws-0Px8k1uRxYVfxvaqDENyYCiwIy8WvidIFCS3ZGbSYb4NQsrl2MlgYQrygVe8v7Omr6zKJYb1i7x3gfl5B6MAw"][14e4:4365]]("https://l.messenger.com/l.php?u=http%3A%2F%2F[14e4%3A4365) (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [%2F&h=AT20D9y7EoQAVVZbLept7KMDerWbvcD48gM9O5ws-0Px8k1uRxYVfxvaqDENyYCiwIy8WvidIFCS3ZGbSYb4NQsrl2MlgYQrygVe8v7Omr6zKJYb1i7x3gfl5B6MAw"][103c:804a]]("https://l.messenger.com/l.php?u=http%3A%2F%2F[103c%3A804a)
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: Primary  Bus: USB
    BD Address: 44:1C:A8:B0:46:6C  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:6994 acl:0 sco:0 events:943 errors:0
    TX bytes:15253 acl:0 sco:0 commands:816 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'amit-PC'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

[    0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0xb2 (or later)
[    0.068752] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.690810] [drm] Finished loading DMC firmware i915/skl_dmc_ver1_26.bin (v1.26)
[    2.278151] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x5e0f01)
[   16.070958] Bluetooth: Core ver 2.22
[   16.070974] Bluetooth: HCI device and connection manager initialized
[   16.070976] Bluetooth: HCI socket layer initialized
[   16.070978] Bluetooth: L2CAP socket layer initialized
[   16.070982] Bluetooth: SCO socket layer initialized
[   16.358396] Bluetooth: hci0: BCM: chip id 70
[   16.359374] Bluetooth: hci0: BCM: features 0x06
[   16.375377] Bluetooth: hci0: amit-PC
[   16.375380] Bluetooth: hci0: BCM (001.001.011) build 0000
[   16.436303] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   16.436306] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   18.460082] Bluetooth: hci0: command 0x1003 tx timeout
[   25.260606] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.260607] Bluetooth: BNEP filters: protocol multicast
[   25.260610] Bluetooth: BNEP socket layer initialized
[   27.804166] Bluetooth: hci0: command 0x1003 tx timeout
[   69.425759] Bluetooth: RFCOMM TTY layer initialized
[   69.425765] Bluetooth: RFCOMM socket layer initialized
[   69.425769] Bluetooth: RFCOMM ver 1.11
[  100.319364] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  116.195558] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  132.322575] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  159.203572] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  175.331367] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  191.201504] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  207.331561] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  223.203601] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  239.331331] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  255.203619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  271.330539] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  287.203621] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  303.331621] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  319.203622] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  335.331573] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  351.203617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  367.332623] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  383.203618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  399.331616] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  415.203636] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  431.331617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  447.203385] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  463.331572] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  479.203577] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  495.331618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  511.204567] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  527.331617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  543.203457] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  559.332622] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  575.203618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  591.331617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  607.203617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  623.331618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  639.203423] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  655.331569] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  671.203618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  687.331617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  703.204576] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  719.331383] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  734.399549] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[  735.203569] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  751.330330] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  767.206360] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  783.331580] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  799.203575] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  815.332437] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  831.203573] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  847.331400] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  863.203610] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  879.331578] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  895.203618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  911.331440] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  927.203605] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  943.332618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  959.203578] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  975.331478] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  991.203576] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1007.331608] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1023.203617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1039.331392] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1055.204631] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1071.332628] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1087.203374] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1103.331602] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1119.203416] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1135.330567] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1151.203617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1167.331563] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1183.203618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1199.331336] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1215.292164] Bluetooth: hci0: command 0x1003 tx timeout
[ 1221.348423] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1237.219578] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1253.347620] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1269.218459] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1285.347619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1301.219618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1317.351455] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1333.220389] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1349.347580] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1365.219608] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1381.347609] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1397.219616] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1413.347581] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1429.219569] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1445.347390] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1461.219580] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1477.348584] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1493.219618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1509.348424] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1525.219618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1541.347618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1557.219473] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1573.347619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1589.220625] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1605.348629] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1621.219620] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1637.347618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1653.219617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1669.347616] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1685.218590] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1701.347575] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1717.219617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1733.347619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1749.219620] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1765.347604] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1781.219616] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1797.347620] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1813.219434] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1829.348617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1845.219614] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1861.348625] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1877.219618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1893.347620] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1909.219618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1925.348618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1941.220481] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1957.347618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1973.219612] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1989.348617] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2005.220625] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2021.347619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2037.220618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2053.347618] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2069.219616] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2085.347610] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2101.219577] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2117.347621] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2133.219519] Bluetooth: hci0: last event is not cmd complete (0x0f)


```

---

### Post by mahardi-baniadam on 2018-08-31
please chek it out here
> [https://dev-pages.info/ubuntu-bluetooth/](https://dev-pages.info/ubuntu-bluetooth/)

---

### Post by Agnishom_Chattopadhyay on 2018-09-02
Running ```
lsusb
``` is not helping. I can only get this much information:

```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) 

```

---

### Post by jeremy31 on 2018-09-02
That tells you that 0a5c:216d is the bluetooth device, so download [https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0a5c-216d.hcd](https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0a5c-216d.hcd)
Then do ```
dmesg | egrep -i 'blue|firm'
```
To see what the file needs to be named

---

### Post by Agnishom_Chattopadhyay on 2018-09-03
When I run the command above, I get the following:

```
42134.236395] Modules linked in: cmac rfcomm bnep nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_hdmi kvm btusb(OE) btrtl btbcm snd_hda_codec_realtek snd_hda_codec_generic snd_soc_skl btintel irqbypass snd_soc_skl_ipc snd_hda_ext_core bluetooth snd_soc_sst_dsp crct10dif_pclmul crc32_pclmul snd_soc_sst_ipc ecdh_generic ghash_clmulni_intel snd_soc_acpi uvcvideo pcbc snd_soc_core videobuf2_vmalloc snd_compress ac97_bus snd_pcm_dmaengine videobuf2_memops videobuf2_v4l2 videobuf2_core aesni_intel videodev aes_x86_64 media snd_hda_intel snd_hda_codec snd_hda_core crypto_simd input_leds snd_hwdep snd_pcm wl(POE) joydev glue_helper serio_raw snd_seq_midi snd_seq_midi_event cryptd hp_wmi sparse_keymap snd_rawmidi cfg80211 intel_cstate intel_rapl_perf mei_me intel_pch_thermal
```

---

### Post by jeremy31 on 2018-09-03
Just rename that downloaded file as /lib/firmware/brcm/BCM.hcd and reboot

---

### Post by Agnishom_Chattopadhyay on 2018-09-13
This worked! Thanks

---

