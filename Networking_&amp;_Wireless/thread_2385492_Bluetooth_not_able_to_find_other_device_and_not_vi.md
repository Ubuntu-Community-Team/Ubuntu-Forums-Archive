---
title: "Bluetooth not able to find other device and not visible on another device"
date: 2018-02-21
forum: Networking &amp; Wireless
---

### Post by vipul220 on 2018-02-21
hi,

Sorry if havent added any perticular detail. Please let me know what extra i ned to provide. Thanks in advance

I am having this issue when i have upgraded to 16.04 from 14.04. My Bluetooth not able to find other devices and not visible on another device. 

there is an error with below command but i am not to find a solution. please help!!!

Here is result for "[COLOR=#000000][FONT=&amp]lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'



[/FONT][/COLOR]```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8131]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 003: ID 05c8:0382 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 005: ID 046d:c535 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 60:6D:C7:F7:AF:B2  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:1001 acl:0 sco:0 events:58 errors:0
    TX bytes:2272 acl:0 sco:0 commands:57 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'vipul-HP-240-G4-Notebook-PC-0'
    Class: 0x0c010c
    Service Classes: Rendering, Capturing
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)


[    0.191498] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.965508] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x5e0f01)
[   10.929725] Bluetooth: Core ver 2.21
[   10.929737] Bluetooth: HCI device and connection manager initialized
[   10.929740] Bluetooth: HCI socket layer initialized
[   10.929742] Bluetooth: L2CAP socket layer initialized
[   10.929746] Bluetooth: SCO socket layer initialized
[   12.317876] Bluetooth: HCI UART driver ver 2.3
[   12.317879] Bluetooth: HCI UART protocol H4 registered
[   12.317880] Bluetooth: HCI UART protocol BCSP registered
[   12.317881] Bluetooth: HCI UART protocol LL registered
[   12.317881] Bluetooth: HCI UART protocol ATH3K registered
[   12.317882] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   12.317904] Bluetooth: HCI UART protocol Intel registered
[   12.317913] Bluetooth: HCI UART protocol BCM registered
[   12.317914] Bluetooth: HCI UART protocol QCA registered
[   13.113470] Bluetooth: hci0: BCM: chip id 70
[   13.129472] Bluetooth: hci0: BCM43142A
[   13.129475] Bluetooth: hci0: BCM (001.001.011) build 0000
[   13.700840] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.700844] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   26.172099] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.172102] Bluetooth: BNEP filters: protocol multicast
[   26.172105] Bluetooth: BNEP socket layer initialized
[   32.384407] audit: type=1400 audit(1519102626.622:58): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.bluetoothctl" pid=1147 comm="apparmor_parser"
[   32.389044] audit: type=1400 audit(1519102626.626:59): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.bluez" pid=1150 comm="apparmor_parser"
[   32.391862] audit: type=1400 audit(1519102626.630:60): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.btmgmt" pid=1152 comm="apparmor_parser"
[   32.394455] audit: type=1400 audit(1519102626.630:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.btmon" pid=1154 comm="apparmor_parser"
[   32.397118] audit: type=1400 audit(1519102626.634:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.hciattach" pid=1156 comm="apparmor_parser"
[   32.402726] audit: type=1400 audit(1519102626.638:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.hciconfig" pid=1158 comm="apparmor_parser"
[   32.405349] audit: type=1400 audit(1519102626.642:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.bluez.hcidump" pid=1160 comm="apparmor_parser"
[   39.987364] audit: type=1400 audit(1519102634.226:73): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1269 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.108497] audit: type=1400 audit(1519102634.346:74): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1267 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   40.242471] audit: type=1400 audit(1519102634.478:75): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1267 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.283125] audit: type=1400 audit(1519102634.522:76): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1397 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.485073] audit: type=1400 audit(1519102634.722:77): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1415 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.490608] audit: type=1400 audit(1519102634.726:78): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1419 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   40.490796] audit: type=1400 audit(1519102634.730:79): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1419 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.737236] audit: type=1400 audit(1519102634.974:80): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=1458 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   40.739596] audit: type=1400 audit(1519102634.978:81): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=1448 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   40.739791] audit: type=1400 audit(1519102634.978:82): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=1448 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   43.359277] Bluetooth: RFCOMM TTY layer initialized
[   43.359283] Bluetooth: RFCOMM socket layer initialized
[   43.359288] Bluetooth: RFCOMM ver 1.11
[ 1987.714684] Bluetooth: hci0: BCM: chip id 70
[ 1987.730702] Bluetooth: hci0: BCM43142A
[ 1987.730726] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1987.730785] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1987.730793] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 1989.736520] Bluetooth: hci0 command 0x1003 tx timeout
[ 8061.541596] Modules linked in: rfcomm bnep binfmt_misc hp_wmi sparse_keymap snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_ipc snd_soc_sst_dsp snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine dw_dmac_core snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event uvcvideo videobuf2_vmalloc intel_rapl x86_pkg_temp_thermal videobuf2_memops intel_powerclamp coretemp videobuf2_v4l2 videobuf2_core v4l2_common btusb btrtl videodev snd_rawmidi snd_seq kvm media snd_seq_device snd_timer irqbypass crct10dif_pclmul crc32_pclmul hci_uart snd ghash_clmulni_intel aesni_intel wl(POE) soundcore aes_x86_64 lrw gf128mul glue_helper btbcm btqca ablk_helper cfg80211 cryptd btintel bluetooth joydev input_leds
[ 8125.335213] Modules linked in: rfcomm bnep binfmt_misc hp_wmi sparse_keymap snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_ipc snd_soc_sst_dsp snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine dw_dmac_core snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event uvcvideo videobuf2_vmalloc intel_rapl x86_pkg_temp_thermal videobuf2_memops intel_powerclamp coretemp videobuf2_v4l2 videobuf2_core v4l2_common btusb btrtl videodev snd_rawmidi snd_seq kvm media snd_seq_device snd_timer irqbypass crct10dif_pclmul crc32_pclmul hci_uart snd ghash_clmulni_intel aesni_intel wl(POE) soundcore aes_x86_64 lrw gf128mul glue_helper btbcm btqca ablk_helper cfg80211 cryptd btintel bluetooth joydev input_leds
[ 8470.829196] Modules linked in: rfcomm bnep binfmt_misc hp_wmi sparse_keymap snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_ipc snd_soc_sst_dsp snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine dw_dmac_core snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event uvcvideo videobuf2_vmalloc intel_rapl x86_pkg_temp_thermal videobuf2_memops intel_powerclamp coretemp videobuf2_v4l2 videobuf2_core v4l2_common btusb btrtl videodev snd_rawmidi snd_seq kvm media snd_seq_device snd_timer irqbypass crct10dif_pclmul crc32_pclmul hci_uart snd ghash_clmulni_intel aesni_intel wl(POE) soundcore aes_x86_64 lrw gf128mul glue_helper btbcm btqca ablk_helper cfg80211 cryptd btintel bluetooth joydev input_leds
[ 8477.499194] Bluetooth: hci0: BCM: chip id 70
[ 8477.515240] Bluetooth: hci0: BCM43142A
[ 8477.515255] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 8477.515303] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 8477.515310] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 8479.521048] Bluetooth: hci0 command 0x1003 tx timeout
[ 9337.207429] [Firmware Bug]: battery: (dis)charge rate invalid.
[ 9913.578187] Bluetooth: hci0 command 0x1003 tx timeout
[14706.992384] Bluetooth: hci0: BCM: chip id 70
[14707.008393] Bluetooth: hci0: BCM43142A
[14707.008405] Bluetooth: hci0: BCM (001.001.011) build 0000
[14708.963347] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[14708.963365] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[14710.966265] Bluetooth: hci0 command 0x1003 tx timeout
[17205.352315] Bluetooth: hci0: BCM: chip id 70
[17205.368369] Bluetooth: hci0: BCM43142A
[17205.368381] Bluetooth: hci0: BCM (001.001.011) build 0000
[17205.368415] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[17205.368420] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[17207.370690] Bluetooth: hci0 command 0x1003 tx timeout
[18877.614014] Bluetooth: hci0: BCM: chip id 70
[18877.630014] Bluetooth: hci0: BCM43142A
[18877.630024] Bluetooth: hci0: BCM (001.001.011) build 0000
[18877.630056] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[18877.630061] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[18879.636126] Bluetooth: hci0 command 0x1003 tx timeout
[19006.817957] Bluetooth: hci0: BCM: chip id 70
[19006.833968] Bluetooth: hci0: BCM43142A
[19006.833977] Bluetooth: hci0: BCM (001.001.011) build 0000
[19006.834010] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[19006.834015] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[19008.839769] Bluetooth: hci0 command 0x1003 tx timeout
[24513.190999] Bluetooth: hci0: BCM: chip id 70
[24513.206999] Bluetooth: hci0: BCM43142A
[24513.207002] Bluetooth: hci0: BCM (001.001.011) build 0000
[24514.518970] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[24514.518992] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[24516.524916] Bluetooth: hci0 command 0x1003 tx timeout
[28777.967386] Bluetooth: hci0: BCM: chip id 70
[28777.983401] Bluetooth: hci0: BCM43142A
[28777.983410] Bluetooth: hci0: BCM (001.001.011) build 0000
[28777.983442] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[28777.983447] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[28779.985600] Bluetooth: hci0 command 0x1003 tx timeout
[29446.832598] Bluetooth: hci0: BCM: chip id 70
[29446.848590] Bluetooth: hci0: BCM43142A
[29446.848601] Bluetooth: hci0: BCM (001.001.011) build 0000
[29446.848633] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[29446.848638] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[29448.854312] Bluetooth: hci0 command 0x1003 tx timeout
[37041.076946] Bluetooth: hci0 urb ffff88021982ad80 failed to resubmit (2)
[37047.324160] Bluetooth: hci0: BCM: chip id 70
[37047.340047] Bluetooth: hci0: vipul-HP-240-G4-Notebook-PC-0
[37047.340064] Bluetooth: hci0: BCM (001.001.011) build 0000
[37047.340116] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[37047.340125] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
```


[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-02-21
Try adding the firmware
```
wget https://www.dropbox.com/s/olqnqevf698lddo/fw-0a5c_216d.hcd
sudo cp fw-0a5c_216d.hcd /lib/firmware/brcm/BCM.hcd
```
Shut down the computer, then boot

---

### Post by vipul220 on 2018-02-22
I have executed code and shutdown then boot

bluetooth fails to start and shows Bluetooth disabled in the setting and Bluetooth disappear from top bar beside wifi sign.


wget [https://www.dropbox.com/s/olqnqevf698lddo/fw-0a5c_216d.hcd](https://www.dropbox.com/s/olqnqevf698lddo/fw-0a5c_216d.hcd)
sudo cp fw-0a5c_216d.hcd /lib/firmware/brcm/BCM.hcd

---

### Post by jeremy31 on 2018-02-22
Lets see if a different source for the firmware works
```
wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-0a5c-216d.hcd
sudo cp BCM43142A0-0a5c-216d.hcd /lib/firmware/brcm/BCM.hcd
```
Shut down and boot again

---

### Post by vipul220 on 2018-02-23
Thanks for helping me ..

after this code now in Bluetooth setting it says "NO Bluetooth adapters found". :(

It was working fine in ubuntu 14.04 but when i upgraded to 16.04 Bluetooth stop working.

---

### Post by vipul220 on 2018-02-23
[COLOR=#000000]Now my Bluetooth is working. I try to reinstall [/COLOR]
[COLOR=#000000]Code:
sudo apt-get install --reinstall linux-headers-generic build-essential[/COLOR]
[COLOR=#000000]After that, compile and install the driver as follows -[/COLOR]
[COLOR=#000000]1) Download the latest backported driver package from here - [/COLOR][http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/")
[COLOR=#000000]2) Copy the downloaded tar.bz2 package to your Ubuntu Desktop > Right-click > Extract here.[/COLOR]
[COLOR=#000000]3) Open a terminal and run the following commands one-by-one [/COLOR]
[COLOR=#000000]Code:
cd Desktop/backports-3.18-rc1-1
make defconfig-ath9k
make
sudo make install[/COLOR]
[COLOR=#000000]4) Reboot for the newer driver to take effect.[/COLOR]

[COLOR=#000000]Now Solved. Thank you bro [/COLOR]:smile:

---

### Post by jeremy31 on 2018-02-23
If that actually worked, it means that your wifi was causing issues with bluetooth as I can see no reason why installing old backports for ath9k wireless would help any with Broadcom wifi/bluetooth

---

