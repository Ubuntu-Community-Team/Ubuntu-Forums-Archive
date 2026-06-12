---
title: "Cant find any bluetooth devices on ubuntu 16.04"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by danipapa on 2017-07-29
Hello.
Yesterday I uninstalled win 10 and installed ubuntu 16.04. I always used my bluetooth speakers for music and movies, but now on ubuntu my laptop cant find any devices ( my android phone either) . I googled some similar problems here, but since im pretty new to ubuntu i think that i made the promlem only worse. Please help me!:) Thank you

---

### Post by jeremy31 on 2017-07-29
Welcome to the forums.
Open a terminal window and enter the following
```
lsusb; rfkill list; dmesg | egrep -i 'blue|firm'
```
Post the results using code tags- see link in my signature

---

### Post by danipapa on 2017-07-29
Thank you for answering me so quickly! This is the result : 
```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:28a2 Sunplus Innovation Technology Inc. Dell Integrated Webcam
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    2.043731] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    3.143128] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   12.136364] Bluetooth: Core ver 2.22
[   12.136378] Bluetooth: HCI device and connection manager initialized
[   12.136380] Bluetooth: HCI socket layer initialized
[   12.136382] Bluetooth: L2CAP socket layer initialized
[   12.136387] Bluetooth: SCO socket layer initialized
[   12.553966] Bluetooth: hci0: BCM: chip id 70
[   12.570008] Bluetooth: hci0: danipapa-Inspiron-3521
[   12.570011] Bluetooth: hci0: BCM (001.001.011) build 0000
[   13.027748] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.027756] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   15.059392] Bluetooth: hci0 command 0x1003 tx timeout
[   22.466489] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.466490] Bluetooth: BNEP filters: protocol multicast
[   22.466493] Bluetooth: BNEP socket layer initialized
[   51.037586] Bluetooth: RFCOMM TTY layer initialized
[   51.037592] Bluetooth: RFCOMM socket layer initialized
[   51.037597] Bluetooth: RFCOMM ver 1.11
[  463.886673] Bluetooth: hci0: BCM: chip id 70
[  463.902695] Bluetooth: hci0: danipapa-Inspiron-3521
[  463.902700] Bluetooth: hci0: BCM (001.001.011) build 0000
[  463.902737] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[  463.902739] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[  465.922737] Bluetooth: hci0 command 0x1003 tx timeout
[ 1372.149286] Bluetooth: hci0: BCM: chip id 70
[ 1372.165311] Bluetooth: hci0: BCM43142A
[ 1372.165316] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1372.165349] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1372.165351] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 1374.175335] Bluetooth: hci0 command 0x1003 tx timeout


```

---

### Post by jeremy31 on 2017-07-30
This should fix it
```
wget https://www.dropbox.com/s/9ryy3ir1tby6wrf/fw-0a5c_21d7.hcd
```
```
sudo cp fw-0a5c_21d7.hcd /lib/firmware/brcm/BCM.hcd
```
Reboot

---

### Post by danipapa on 2017-07-30
It didnt work, so I reinstalled ubuntu, and tried it so. Now the bluetooth icon is gone from the upper bar, and if i open the BT settings from the system manager, it says that its disabled, even though the button says "ON". Now the first code gave me this : 
```
danipapa@danipapa-Inspiron-3521:~$ lsusb; rfkill list; dmesg | egrep -i 'blue|firm'
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:28a2 Sunplus Innovation Technology Inc. Dell Integrated Webcam
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    2.043565] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    3.168155] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   30.202569] Bluetooth: Core ver 2.22
[   30.202585] Bluetooth: HCI device and connection manager initialized
[   30.202587] Bluetooth: HCI socket layer initialized
[   30.202589] Bluetooth: L2CAP socket layer initialized
[   30.202594] Bluetooth: SCO socket layer initialized
[   30.681726] Bluetooth: hci0: BCM: chip id 70
[   30.697713] Bluetooth: hci0: BCM43142A
[   30.697716] Bluetooth: hci0: BCM (001.001.011) build 0000
[   32.911278] Bluetooth: hci0 command 0x213c tx timeout
[   40.942770] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[   42.958688] Bluetooth: hci0 command 0x0c03 tx timeout
[   47.147433] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   47.147435] Bluetooth: BNEP filters: protocol multicast
[   47.147442] Bluetooth: BNEP socket layer initialized
[   51.182176] Bluetooth: hci0: BCM: Reset failed (-110)
[   53.198025] Bluetooth: hci0 command 0x0c03 tx timeout
[   61.421426] Bluetooth: hci0: BCM: Reset failed (-110)


```

Thank you for helping me, it means a lot! I'm a beginner user, and i simply get dizzy from these lines....

---

### Post by danipapa on 2017-08-03
I'm tried different ways, but its still not working. Now if i type in the code that you wrote first it gives this. This state is after a fresh reinstallation of the whole system with full reset, and I also typed in the 2 codes that you wrote for the 2nd time. 
```
lsusb; rfkill list; dmesg | egrep -i 'blue|firm'
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:28a2 Sunplus Innovation Technology Inc. Dell Integrated Webcam
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    2.033039] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    3.136813] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   10.589326] Bluetooth: Core ver 2.21
[   10.589339] Bluetooth: HCI device and connection manager initialized
[   10.589342] Bluetooth: HCI socket layer initialized
[   10.589344] Bluetooth: L2CAP socket layer initialized
[   10.589348] Bluetooth: SCO socket layer initialized
[   12.692611] Bluetooth: hci0 command 0x1001 tx timeout
[   20.720517] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   20.736849] Bluetooth: hci0: BCM: chip id 70
[   20.752860] Bluetooth: hci0: danipapa-Inspiron-3521
[   20.752864] Bluetooth: hci0: BCM (001.001.011) build 0000
[   23.248450] Bluetooth: hci0 command 0x213c tx timeout
[   31.472228] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[   33.520237] Bluetooth: hci0 command 0x0c03 tx timeout
[   36.658627] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.658628] Bluetooth: BNEP filters: protocol multicast
[   36.658631] Bluetooth: BNEP socket layer initialized
[   41.712042] Bluetooth: hci0: BCM: Reset failed (-110)


```
Please help me !

---

### Post by jeremy31 on 2017-08-05
It could be an issue with the timing of the firmware upload, try
```
sudo modprobe -r btusb && sleep 20 && sudo modprobe btusb
```
Then see if it works

---

### Post by 233mhz on 2018-03-01
I have the same problem. I try this solution but nothing happens


```


Bus 001 Device 005: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 004: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 003: ID 0951:162d Kingston Technology DataTraveler 102
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    0.086544] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.333326] [Firmware Bug]: Invalid critical threshold (0)
[   16.747331] snd_hda_intel 0000:00:03.0: Applying patch firmware 'hda-jack-retask.fw'
[   16.747558] snd_hda_intel 0000:00:1b.0: Applying patch firmware 'hda-jack-retask.fw'
[   17.180618] Bluetooth: Core ver 2.22
[   17.180642] Bluetooth: HCI device and connection manager initialized
[   17.180645] Bluetooth: HCI socket layer initialized
[   17.180647] Bluetooth: L2CAP socket layer initialized
[   17.180654] Bluetooth: SCO socket layer initialized
[   17.298686] Bluetooth: hci0: BCM: chip id 70
[   17.299663] Bluetooth: hci0: BCM: features 0x06
[   17.315680] Bluetooth: hci0: BCM43142A
[   17.315684] Bluetooth: hci0: BCM (001.001.011) build 0000
[   19.492062] Bluetooth: hci0 command 0x213c tx timeout
[   27.616022] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[   29.632041] Bluetooth: hci0 command 0x0c03 tx timeout
[   37.856075] Bluetooth: hci0: BCM: Reset failed (-110)
[   38.501847] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.501850] Bluetooth: BNEP filters: protocol multicast
[   38.501854] Bluetooth: BNEP socket layer initialized
[   39.872105] Bluetooth: hci0 command 0x0c03 tx timeout
[   48.096101] Bluetooth: hci0: BCM: Reset failed (-110)
[  179.360975] Modules linked in: bnep nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic btusb btrtl btbcm btintel bluetooth ecdh_generic uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media wl(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel aes_x86_64 crypto_simd glue_helper cryptd intel_cstate intel_rapl_perf snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm input_leds joydev serio_raw hp_wmi sparse_keymap wmi_bmof snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq lpc_ich snd_seq_device cfg80211 snd_timer snd mei_me shpchp mei soundcore hp_accel mac_hid lis3lv02d hp_wireless input_polldev intel_smartconnect parport_pc ppdev lp parport
[  204.986303] Bluetooth: hci0 command 0x0c03 tx timeout
[  213.209100] Bluetooth: hci0: BCM: Reset failed (-110)
[  215.224964] Bluetooth: hci0 command 0x0c03 tx timeout
[  223.448330] Bluetooth: hci0: BCM: Reset failed (-110)
```

---

### Post by ayushchaurasia on 2018-06-18
I have the same problem and tried above solution but now it shows bluetooth disabled. Below is log.


```
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 020: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
[ 0.168103] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 12.718840] Bluetooth: Core ver 2.21
[ 12.718862] Bluetooth: HCI device and connection manager initialized
[ 12.718864] Bluetooth: HCI socket layer initialized
[ 12.718867] Bluetooth: L2CAP socket layer initialized
[ 12.718873] Bluetooth: SCO socket layer initialized
[ 13.118111] Bluetooth: hci0: BCM: chip id 70
[ 13.134116] Bluetooth: hci0: BCM43142A
[ 13.134120] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 13.545913] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 13.545918] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 14.061395] hid-rmi 0018:06CB:2985.0001: firmware id: 1567123
[ 15.552114] Bluetooth: hci0 command 0x1003 tx timeout
[ 27.040196] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 27.040199] Bluetooth: BNEP filters: protocol multicast
[ 27.040203] Bluetooth: BNEP socket layer initialized
[ 27.734469] Bluetooth: RFCOMM TTY layer initialized
[ 27.734476] Bluetooth: RFCOMM socket layer initialized
[ 27.734487] Bluetooth: RFCOMM ver 1.11
[ 5185.540020] Bluetooth: hci0: BCM: chip id 70
[ 5185.556029] Bluetooth: hci0: BCM43142A
[ 5185.556035] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 5185.556052] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 5185.556054] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 5187.561592] Bluetooth: hci0 command 0x1003 tx timeout
[ 5210.329341] Bluetooth: hci0 command 0x1003 tx timeout
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
[ 0.172875] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 12.239525] Bluetooth: Core ver 2.21
[ 12.239548] Bluetooth: HCI device and connection manager initialized
[ 12.239552] Bluetooth: HCI socket layer initialized
[ 12.239555] Bluetooth: L2CAP socket layer initialized
[ 12.239561] Bluetooth: SCO socket layer initialized
[ 12.669926] Bluetooth: hci0: BCM: chip id 70
[ 12.685925] Bluetooth: hci0: vyali-Inspiron-3543
[ 12.685930] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 14.213886] hid-rmi 0018:06CB:2985.0001: firmware id: 1567123
[ 15.327987] Bluetooth: hci0 command 0x213c tx timeout
[ 23.323099] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[ 25.326892] Bluetooth: hci0 command 0x0c03 tx timeout
[ 33.321967] Bluetooth: hci0: BCM: Reset failed (-110)
[ 35.325745] Bluetooth: hci0 command 0x0c03 tx timeout
[ 39.734491] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 39.734495] Bluetooth: BNEP filters: protocol multicast
[ 39.734500] Bluetooth: BNEP socket layer initialized
[ 43.320918] Bluetooth: hci0: BCM: Reset failed (-110)
[ 374.743130] Bluetooth: hci0 command 0x0c03 tx timeout
[ 382.741112] Bluetooth: hci0: BCM: Reset failed (-110)
[ 384.745456] Bluetooth: hci0 command 0x0c03 tx timeout
[ 392.742899] Bluetooth: hci0: BCM: Reset failed (-110)
```

---

### Post by jeremy31 on 2018-06-18
> **ayushchaurasia said:**
> I have the same problem and tried above solution but now it shows bluetooth disabled. Below is log.


```
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 020: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
[ 0.168103] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 12.718840] Bluetooth: Core ver 2.21
[ 12.718862] Bluetooth: HCI device and connection manager initialized
[ 12.718864] Bluetooth: HCI socket layer initialized
[ 12.718867] Bluetooth: L2CAP socket layer initialized
[ 12.718873] Bluetooth: SCO socket layer initialized
[ 13.118111] Bluetooth: hci0: BCM: chip id 70
[ 13.134116] Bluetooth: hci0: BCM43142A
[ 13.134120] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 13.545913] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 13.545918] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 14.061395] hid-rmi 0018:06CB:2985.0001: firmware id: 1567123
[ 15.552114] Bluetooth: hci0 command 0x1003 tx timeout
[ 27.040196] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 27.040199] Bluetooth: BNEP filters: protocol multicast
[ 27.040203] Bluetooth: BNEP socket layer initialized
[ 27.734469] Bluetooth: RFCOMM TTY layer initialized
[ 27.734476] Bluetooth: RFCOMM socket layer initialized
[ 27.734487] Bluetooth: RFCOMM ver 1.11
[ 5185.540020] Bluetooth: hci0: BCM: chip id 70
[ 5185.556029] Bluetooth: hci0: BCM43142A
[ 5185.556035] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 5185.556052] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 5185.556054] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 5187.561592] Bluetooth: hci0 command 0x1003 tx timeout
[ 5210.329341] Bluetooth: hci0 command 0x1003 tx timeout
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
[ 0.172875] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[ 12.239525] Bluetooth: Core ver 2.21
[ 12.239548] Bluetooth: HCI device and connection manager initialized
[ 12.239552] Bluetooth: HCI socket layer initialized
[ 12.239555] Bluetooth: L2CAP socket layer initialized
[ 12.239561] Bluetooth: SCO socket layer initialized
[ 12.669926] Bluetooth: hci0: BCM: chip id 70
[ 12.685925] Bluetooth: hci0: vyali-Inspiron-3543
[ 12.685930] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 14.213886] hid-rmi 0018:06CB:2985.0001: firmware id: 1567123
[ 15.327987] Bluetooth: hci0 command 0x213c tx timeout
[ 23.323099] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[ 25.326892] Bluetooth: hci0 command 0x0c03 tx timeout
[ 33.321967] Bluetooth: hci0: BCM: Reset failed (-110)
[ 35.325745] Bluetooth: hci0 command 0x0c03 tx timeout
[ 39.734491] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 39.734495] Bluetooth: BNEP filters: protocol multicast
[ 39.734500] Bluetooth: BNEP socket layer initialized
[ 43.320918] Bluetooth: hci0: BCM: Reset failed (-110)
[ 374.743130] Bluetooth: hci0 command 0x0c03 tx timeout
[ 382.741112] Bluetooth: hci0: BCM: Reset failed (-110)
[ 384.745456] Bluetooth: hci0 command 0x0c03 tx timeout
[ 392.742899] Bluetooth: hci0: BCM: Reset failed (-110)
```

Try shutting the computer off, then boot

---

