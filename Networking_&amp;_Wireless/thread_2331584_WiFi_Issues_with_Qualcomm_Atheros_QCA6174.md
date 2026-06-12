---
title: "WiFi Issues with Qualcomm Atheros QCA6174?"
date: 2016-07-23
forum: Networking &amp; Wireless
---

### Post by snaysler on 2016-07-23
Hey guys, so I'm relatively new to Ubuntu and just installed Ubuntu 16.04 on my laptop (MSI gt72 dominator...)

I love it, and I finally got pretty much everything working, but I'm having one very frustrating issue. Wifi works just fine, but my connection to the internet will stop working a few times an hour. I'll remain connected to a WiFi network, good signal, but the internet will just stop working. I then disconnect and reconnect and it works again. This makes gaming and other things a real pain. Is there a wireless driver I should install that's more reliable than whatever one I'm using now? Also, I've noticed a general slowdown in speed. I used to get around 60 Mb/s, now I'm at around 8 Mb/s.

My Wireless Card:
Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 20)

More Info:
```
  *-network
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 20
       serial: 10:08:b1:8a:9e:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-31-generic firmware=SW_RM.1.1.1-00157-QCARMSWPZ-1 ip=192.168.1.19 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by chili555 on 2016-07-23
I am a bit suspicious of your firmware. Please let us see:```
dmesg | grep ath
ls /lib/firmware/ath10k/QCA6174/hw2.1
ls /lib/firmware/ath10k/QCA6174/hw3.0
```Thanks.

---

### Post by snaysler on 2016-07-23
dmesg | grep ath
```

[    2.352855] ath3k: probe of 1-1.3:1.0 failed with error -2
[    2.352878] usbcore: registered new interface driver ath3k
[    2.386143] ath10k_pci 0000:04:00.0: enabling device (0000 -> 0002)
[    2.386464] ath10k_pci 0000:04:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.626865] ath10k_pci 0000:04:00.0: Direct firmware load for ath10k/cal-pci-0000:04:00.0.bin failed with error -2
[    4.125105] ath10k_pci 0000:04:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff sub 1a56:1525) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[    4.125109] ath10k_pci 0000:04:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.201581] ath: EEPROM regdomain: 0x6c
[    4.201583] ath: EEPROM indicates we should expect a direct regpair map
[    4.201584] ath: Country alpha2 being used: 00
[    4.201585] ath: Regpair used: 0x6c
[    4.206386] ath10k_pci 0000:04:00.0 wlp4s0: renamed from wlan0
[ 2113.563604] ath10k_pci 0000:04:00.0: firmware crashed! (uuid 56cf0659-99f7-4d56-8a64-b71578eb6f13)
[ 2113.563610] ath10k_pci 0000:04:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff sub 1a56:1525) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[ 2113.563612] ath10k_pci 0000:04:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2113.565612] ath10k_pci 0000:04:00.0: firmware register dump:
[ 2113.565614] ath10k_pci 0000:04:00.0: [00]: 0x05010000 0x000015B3 0x000A773B 0x00955B31
[ 2113.565615] ath10k_pci 0000:04:00.0: [04]: 0x000A773B 0x00060130 0x00000004 0x00000000
[ 2113.565616] ath10k_pci 0000:04:00.0: [08]: 0x00955A00 0x0040D4B8 0x004084F0 0x004207E4
[ 2113.565617] ath10k_pci 0000:04:00.0: [12]: 0x00000009 0x00000000 0x0096BDC8 0x0096BDDE
[ 2113.565618] ath10k_pci 0000:04:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x009287BD
[ 2113.565619] ath10k_pci 0000:04:00.0: [20]: 0x400A773B 0x0041A710 0x004207C0 0x00400000
[ 2113.565620] ath10k_pci 0000:04:00.0: [24]: 0x800B4405 0x0041A770 0x00000001 0xC00A773B
[ 2113.565621] ath10k_pci 0000:04:00.0: [28]: 0x809A6C34 0x0041A8E0 0x0042932C 0x0042CA20
[ 2113.565622] ath10k_pci 0000:04:00.0: [32]: 0x809A6288 0x0041A920 0x0041A948 0x00427130
[ 2113.565623] ath10k_pci 0000:04:00.0: [36]: 0x80934BAE 0x0041A940 0x0042D094 0x00000002
[ 2113.565624] ath10k_pci 0000:04:00.0: [40]: 0x809C2D4F 0x0041A9E0 0x0043557C 0x00427788
[ 2113.565625] ath10k_pci 0000:04:00.0: [44]: 0x809BD030 0x0041AA00 0x0043557C 0x00000001
[ 2113.565626] ath10k_pci 0000:04:00.0: [48]: 0x809291E8 0x0041AA50 0x00000010 0x00404170
[ 2113.565627] ath10k_pci 0000:04:00.0: [52]: 0x800B22BD 0x0041AAA0 0x00400000 0x00000000
[ 2113.565628] ath10k_pci 0000:04:00.0: [56]: 0x800A00A2 0x0041AAC0 0x0040D3D0 0x00000F00
[ 2115.101358] ath10k_pci 0000:04:00.0: device successfully recovered
[69064.746438] ath10k_pci 0000:04:00.0: firmware crashed! (uuid ce196239-c390-47df-b0db-4e5048e9f22a)
[69064.746451] ath10k_pci 0000:04:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff sub 1a56:1525) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[69064.746454] ath10k_pci 0000:04:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[69064.748455] ath10k_pci 0000:04:00.0: firmware register dump:
[69064.748458] ath10k_pci 0000:04:00.0: [00]: 0x05010000 0x000015B3 0x000A773B 0x00955B31
[69064.748460] ath10k_pci 0000:04:00.0: [04]: 0x000A773B 0x00060130 0x00000004 0x00000000
[69064.748462] ath10k_pci 0000:04:00.0: [08]: 0x00955A00 0x0040D4B8 0x004084F0 0x004207E4
[69064.748463] ath10k_pci 0000:04:00.0: [12]: 0x00000009 0x00000000 0x0096BDC8 0x0096BDDE
[69064.748465] ath10k_pci 0000:04:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x009287BD
[69064.748467] ath10k_pci 0000:04:00.0: [20]: 0x400A773B 0x0041A710 0x004207C0 0x00400000
[69064.748468] ath10k_pci 0000:04:00.0: [24]: 0x800B4405 0x0041A770 0x00000001 0xC00A773B
[69064.748470] ath10k_pci 0000:04:00.0: [28]: 0x809A6C34 0x0041A8E0 0x0042932C 0x0042CA20
[69064.748472] ath10k_pci 0000:04:00.0: [32]: 0x809A6288 0x0041A920 0x0041A948 0x00427130
[69064.748475] ath10k_pci 0000:04:00.0: [36]: 0x80934BAE 0x0041A940 0x0042D094 0x00000002
[69064.748476] ath10k_pci 0000:04:00.0: [40]: 0x809C2D4F 0x0041A9E0 0x0043557C 0x00427788
[69064.748478] ath10k_pci 0000:04:00.0: [44]: 0x809BD030 0x0041AA00 0x0043557C 0x00000001
[69064.748479] ath10k_pci 0000:04:00.0: [48]: 0x809291E8 0x0041AA50 0x00000010 0x00404170
[69064.748481] ath10k_pci 0000:04:00.0: [52]: 0x800B22BD 0x0041AAA0 0x00400000 0x00000000
[69064.748482] ath10k_pci 0000:04:00.0: [56]: 0x800A00A2 0x0041AAC0 0x0040D3D0 0x00000F00
[69066.283665] ath10k_pci 0000:04:00.0: device successfully recovered
[69085.811072] ath10k_pci 0000:04:00.0: no channel configured; ignoring frame(s)!
[70096.320996] ath10k_pci 0000:04:00.0: no channel configured; ignoring frame(s)!
[70401.917000] ath10k_pci 0000:04:00.0: firmware crashed! (uuid 4bcead36-9be1-41d6-8f5f-5ce93fa27ec1)
[70401.917016] ath10k_pci 0000:04:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff sub 1a56:1525) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[70401.917019] ath10k_pci 0000:04:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[70401.919022] ath10k_pci 0000:04:00.0: firmware register dump:
[70401.919026] ath10k_pci 0000:04:00.0: [00]: 0x05010000 0x000015B3 0x000A773B 0x00955B31
[70401.919038] ath10k_pci 0000:04:00.0: [04]: 0x000A773B 0x00060130 0x00000004 0x00000000
[70401.919040] ath10k_pci 0000:04:00.0: [08]: 0x00955A00 0x0040D4B8 0x004084F0 0x004207E4
[70401.919043] ath10k_pci 0000:04:00.0: [12]: 0x00000009 0x00000000 0x0096BDC8 0x0096BDDE
[70401.919045] ath10k_pci 0000:04:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x009287BD
[70401.919056] ath10k_pci 0000:04:00.0: [20]: 0x400A773B 0x0041A710 0x004207C0 0x00400000
[70401.919059] ath10k_pci 0000:04:00.0: [24]: 0x800B4405 0x0041A770 0x00000001 0xC00A773B
[70401.919061] ath10k_pci 0000:04:00.0: [28]: 0x809A6C34 0x0041A8E0 0x0042932C 0x0042CA20
[70401.919063] ath10k_pci 0000:04:00.0: [32]: 0x809A6288 0x0041A920 0x0041A948 0x00427130
[70401.919065] ath10k_pci 0000:04:00.0: [36]: 0x80934BAE 0x0041A940 0x0042D094 0x00000002
[70401.919068] ath10k_pci 0000:04:00.0: [40]: 0x809C2D4F 0x0041A9E0 0x0043557C 0x00427788
[70401.919070] ath10k_pci 0000:04:00.0: [44]: 0x809BD030 0x0041AA00 0x0043557C 0x00000001
[70401.919072] ath10k_pci 0000:04:00.0: [48]: 0x809291E8 0x0041AA50 0x00000010 0x00404170
[70401.919074] ath10k_pci 0000:04:00.0: [52]: 0x800B22BD 0x0041AAA0 0x00400000 0x00000000
[70401.919076] ath10k_pci 0000:04:00.0: [56]: 0x800A00A2 0x0041AAC0 0x0040D3D0 0x00000F00
[70403.458955] ath10k_pci 0000:04:00.0: device successfully recovered

```

ls /lib/firmware/ath10k/QCA6174/hw2.1
```

board-2.bin  board.bin  firmware-5.bin  notice_ath10k_firmware-5.txt

```

ls /lib/firmware/ath10k/QCA6174/hw3.0
```

board-2.bin  board.bin  firmware-4.bin  notice_ath10k_firmware-4.txt

```

---

### Post by snaysler on 2016-07-23
Any insights?

> **chili555 said:**
> I am a bit suspicious of your firmware. Please let us see:```
dmesg | grep ath
ls /lib/firmware/ath10k/QCA6174/hw2.1
ls /lib/firmware/ath10k/QCA6174/hw3.0
```Thanks.

---

### Post by chili555 on 2016-07-23
Wow! The driver, firmware and hardware are very unhappy. The firmware crashes and reloads periodically which, I'm sure, leads to disconnects, instability, etc. > qca6174 hw2.1 Let's have a closer look at the firmware in hw2.1.```
md5sum /lib/firmware/ath10k/QCA6174/hw2.1/*
```For reference, the latest that's available is:```
ee53cb8601568f2693043f8fe47677c1  linux-firmware_1.158_all/data/lib/firmware/ath10k/QCA6174/hw2.1/board-2.bin
461e7f4b2f32f1c4ef50d26f76b715eb  linux-firmware_1.158_all/data/lib/firmware/ath10k/QCA6174/hw2.1/board.bin
944ef57488e09e708222d4fb49c3ab73  linux-firmware_1.158_all/data/lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
520e814a78b09b4e29c65ba3ddac5631  linux-firmware_1.158_all/data/lib/firmware/ath10k/QCA6174/hw2.1/notice_ath10k_firmware-5.txt
```If yours is different, suggesting a different version, or else corrupted, we'll replace it.

---

### Post by jeremy31 on 2016-07-23
The poster might be helped with kvallo's newer board-2.bin from [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1) as it appears to support the subsystem ID
```
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo rm board-2.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw2.1/board-2.bin
```

Reboot

For anyone that cares where that info is from, you can use the strings command on the board-2.bin file, ```
strings /lib/firmware/ath10k/QCA6174/hw2.1/board-2.bin | grep version
```
I have linux-firmware from Yakkety and it doesn't list the subsystem ID corresponding with 1a56:1525 but the newer board-2.bin from kvallo contains ```
bus=pci,vendor=168c,device=003e,subsystem-vendor=1a56,subsystem-device=1525m
```

---

### Post by chili555 on 2016-07-23
> **jeremy31 said:**
> The poster might be helped with kvallo's newer board-2.bin from [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1) as it appears to support the subsystem ID
```
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo rm board-2.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw2.1/board-2.bin
```

Reboot

For anyone that cares where that info is from, you can use the strings command on the board-2.bin file, ```
strings /lib/firmware/ath10k/QCA6174/hw2.1/board-2.bin | grep version
```
I have linux-firmware from Yakkety and it doesn't list the subsystem ID corresponding with 1a56:1525 but the newer board-2.bin from kvallo contains ```
bus=pci,vendor=168c,device=003e,subsystem-vendor=1a56,subsystem-device=1525m
```Awesome information, Jeremy! Thanks.

---

