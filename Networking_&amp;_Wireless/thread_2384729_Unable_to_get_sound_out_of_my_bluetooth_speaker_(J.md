---
title: "Unable to get sound out of my bluetooth speaker (JBL pulse 2)"
date: 2018-02-11
forum: Networking &amp; Wireless
---

### Post by fabienlege on 2018-02-11
Hi !

I try to get my conputer sound get out from my bluetooth speaker without success

**About my system :**
- Ubuntu 16.04 (gnome)
 - kernel : 4.13.0-32-generic

[B]Problem :
[/B] - Bluetooth logo appear on top right corner of my screen
 - I find my speaker in bluetooth devices list and pair it with my computer
 - pairing work well but sound get out from integrated speakers of my computer (not from my bluetooth speaker)

[B]What i've already tried :
[/B] - Go to Setting > sounds > Output but i've only integrated speakers in the list
- Install pavucontrol > my bluetooth speaker doesn't appear- Install blueman to pair my bluetooth speaker as "headset" and "audio synchronie".when i right click on my bluettoth speaker in blueman, "audio profile" seem to be empty. [B]

Some logs :
[/B]```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth Linux fabien-sabre-15 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:850a]
    Kernel driver in use: r8169
    Kernel modules: r8169
04:00.0 Network controller [0280]: Intel Corporation Device [8086:24fb] (rev 10)
    Subsystem: Intel Corporation Device [8086:2110]
    Kernel driver in use: iwlwifi
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0aa7 Intel Corp. 
Bus 001 Device 002: ID 04f2:b59e Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.689308] Bluetooth: Core ver 2.22
[    2.689318] Bluetooth: HCI device and connection manager initialized
[    2.689321] Bluetooth: HCI socket layer initialized
[    2.689322] Bluetooth: L2CAP socket layer initialized
[    2.689325] Bluetooth: SCO socket layer initialized
[    2.740371] Bluetooth: HCI UART driver ver 2.3
[    2.740373] Bluetooth: HCI UART protocol H4 registered
[    2.740373] Bluetooth: HCI UART protocol BCSP registered
[    2.740384] Bluetooth: HCI UART protocol LL registered
[    2.740384] Bluetooth: HCI UART protocol ATH3K registered
[    2.740385] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    2.740402] Bluetooth: HCI UART protocol Intel registered
[    2.740411] Bluetooth: HCI UART protocol Broadcom registered
[    2.740412] Bluetooth: HCI UART protocol QCA registered
[    2.740412] Bluetooth: HCI UART protocol AG6XX registered
[    2.740413] Bluetooth: HCI UART protocol Marvell registered
[    2.749017] Bluetooth: hci0: read Intel version: 370810225019140f00
[    2.753862] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-22.50.19.14.f.bseq
[    2.897596] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.959709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.959710] Bluetooth: BNEP filters: protocol multicast
[    4.959712] Bluetooth: BNEP socket layer initialized
[   15.249510] Bluetooth: RFCOMM TTY layer initialized
[   15.249515] Bluetooth: RFCOMM socket layer initialized
[   15.249519] Bluetooth: RFCOMM ver 1.11
[    0.098162] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.144516] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    2.753862] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-22.50.19.14.f.bseq
[    2.765858] iwlwifi 0000:04:00.0: loaded firmware version 29.610311.0 op_mode iwlmvm
[    2.897596] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
bluetooth             544768  39 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
```
```
sudo service bluetooth status
[sudo] Mot de passe de fabien : 
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since jeu. 2018-02-08 21:22:33 CET; 20min ago
     Docs: man:bluetoothd(8)
 Main PID: 986 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;986 /usr/lib/bluetooth/bluetoothd

févr. 08 21:22:33 fabien-sabre-15 bluetoothd[986]: Not enough free handles to register service
févr. 08 21:22:33 fabien-sabre-15 bluetoothd[986]: Sap driver initialization failed.
févr. 08 21:22:33 fabien-sabre-15 bluetoothd[986]: sap-server: Operation not permitted (1)
févr. 08 21:22:33 fabien-sabre-15 systemd[1]: Started Bluetooth service.
févr. 08 21:22:43 fabien-sabre-15 bluetoothd[986]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSource
févr. 08 21:22:43 fabien-sabre-15 bluetoothd[986]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSink
févr. 08 21:22:56 fabien-sabre-15 bluetoothd[986]: Endpoint registered: sender=:1.105 path=/MediaEndpoint/A2DPSource
févr. 08 21:22:56 fabien-sabre-15 bluetoothd[986]: Endpoint registered: sender=:1.105 path=/MediaEndpoint/A2DPSink
févr. 08 21:22:56 fabien-sabre-15 bluetoothd[986]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
févr. 08 21:22:58 fabien-sabre-15 bluetoothd[986]: /org/bluez/hci0/dev_B8_69_C2_84_D4_7B/fd0: fd(22) ready
```
```

dpkg -l | grep blue
ii  bluez                                   5.37-0ubuntu5.1                            amd64        Bluetooth tools and daemons
ii  bluez-cups                              5.37-0ubuntu5.1                            amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                             5.37-0ubuntu5.1                            amd64        bluez obex daemon
ii  gir1.2-gnomebluetooth-1.0:amd64         3.18.2-1ubuntu2                            amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth                         3.18.2-1ubuntu2                            amd64        GNOME Bluetooth tools
ii  indicator-bluetooth                     0.0.6+16.04.20160526-0ubuntu1              amd64        System bluetooth indicator.
ii  libbluetooth3:amd64                     5.37-0ubuntu5.1                            amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64              3.18.2-1ubuntu2                            amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth             1:8.0-0ubuntu3.7                           amd64        Bluetooth module for PulseAudio sound server
```
```
sudo rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

If an expert have any idea...

Thank's in advance

---

### Post by jeremy31 on 2018-02-11
What are the results for ```
pactl list short
```

---

### Post by fabienlege on 2018-02-11
Here the output of command :
```
pactl list short
0    module-device-restore        
1    module-stream-restore        
2    module-card-restore        
3    module-augment-properties        
4    module-switch-on-port-available        
5    module-udev-detect        
6    module-alsa-card    device_id="0" name="pci-0000_00_1f.3" card_name="alsa_card.pci-0000_00_1f.3" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"    
7    module-bluetooth-policy        
8    module-bluetooth-discover        
9    module-bluez5-discover        
10    module-native-protocol-unix        
11    module-default-device-restore        
12    module-rescue-streams        
13    module-always-sink        
14    module-intended-roles        
15    module-suspend-on-idle        
16    module-systemd-login        
17    module-position-event-sounds        
18    module-filter-heuristics        
19    module-filter-apply        
20    module-x11-publish    display=:1    
21    module-x11-bell    display=:1 sample=bell.ogg    
22    module-x11-cork-request    display=:1    
23    module-x11-xsmp    display=:1 session_manager=local/fabien-sabre-15:@/tmp/.ICE-unix/2076,unix/fabien-sabre-15:/tmp/.ICE-unix/2076    
0    alsa_output.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
0    alsa_output.pci-0000_00_1f.3.analog-stereo.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
1    alsa_input.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
0    module-systemd-login.c    (null)
2    protocol-native.c    gnome-settings-daemon
6    module-x11-xsmp.c    (null)
7    protocol-native.c    gnome-shell
8    protocol-native.c    gnome-shell
25    protocol-native.c    gnome-settings-daemon
60    protocol-native.c    gnome-settings-daemon
115    module-systemd-login.c    (null)
124    protocol-native.c    firefox
125    protocol-native.c    firefox
126    protocol-native.c    firefox
127    protocol-native.c    pactl
0    audio-volume-change    s16le 2ch 44100Hz    0,067
1    bell-window-system    s16le 2ch 44100Hz    0,139
0    alsa_card.pci-0000_00_1f.3    module-alsa-card.c

```

thanks for your help

---

### Post by mc4man on 2018-02-12
Noting that pairing & connecting are 2 separate things, you could try this in 16.04
Get rid of blueman if installed.
Open bluetooth settings > if your speaker is listed remove it (highlight, then click the - button), close bluetooth settings.

In a terminal go 
```
sudo -H gedit /etc/pulse/default.pa
```
Add this under the .ifexists module-bluetooth-discover.so section  (about line 73, screen
 ```
.ifexists module-switch-on-connect.so
load-module module-switch-on-connect
.endif

```

reboot

Turn on speaker
Open up bluetooth settings, wait til it finds device, add it. It should then autoconnect. (In bluetooth indicator dropdown the device would be shown, highlighting the device would show " connection on" the device

So here when I turn on the speaker it automatically connects & is used. The only caveat here is if I connect the speaker in another ubuntu install then I have to remove & re-add speaker in this install. Connecting the speaker to android devices does not cause this, just another ubuntu install. Why no idea, maybe the speaker, maybe some linux bluetooth nonsense..

---

### Post by fabienlege on 2018-02-17
Thanks for your reply

I've tried your solution but it changing nothing ...

My speaker always seem to pairing weel but it always absent of "outputs" in pulseaudio panel...

---

### Post by mc4man on 2018-02-17
> **fabienlege said:**
> Thanks for your reply

I've tried your solution but it changing nothing ...

My speaker always seem to pairing weel but it always absent of "outputs" in pulseaudio panel...
It won't show in pulseaudio if not connected. When you set it up in bluetooth settings does the speaker connect?
screen 1 shows speaker paired but not connected
screen 2 shows speaker paired & connected

Which is yours?

---

