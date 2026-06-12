---
title: "No wifi nor bluetooth capability"
date: 2022-02-14
forum: Networking &amp; Wireless
---

### Post by him610 on 2022-02-14
Discovered today that I had neither bluetooth nor wireless internet capability. When installed May 2021 ago both were present and operational. 

Ubuntu 20.04.3 LTS
Linux h270m 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

$ inxi -MCNxx
Machine:   Type: Desktop Mobo: ASRock model: H270M-ITX/ac serial: <superuser/root required> 
           UEFI: American Megatrends v: P2.50 date: 03/16/2018 
CPU:       Topology: Dual Core model: Intel Pentium G4560 bits: 64 type: MT MCP 
           arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 27999 
           Speed: 800 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 
           4: 800 
Network:   Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: kernel 
           port: f000 bus ID: 00:1f.6 chip ID: 8086:15b8 
           Device-2: Intel I211 Gigabit Network vendor: ASRock driver: igb v: kernel 
           port: d000 bus ID: 03:00.0 chip ID: 8086:1539 
           Device-3: Intel Wireless 3160 driver: N/A port: d000 bus ID: 04:00.0 
           chip ID: 8086:08b3 

```

Here is what I have found so far...
```
$ modinfo  iwlwifi
modinfo: ERROR: Module iwlwifi not found.

```
May or may not be helpful; my other non-affected machine has version 1.187.25
```
$ dpkg -l | grep linux-firm*
ii  linux-firmware                            1.187.26                              all          Firmware for Linux kernel drivers

```
Bluetooth information  
```
$ dpkg -l | grep blue
ii  blueman                                   2.1.2-1ubuntu0.3                      amd64        Graphical bluetooth manager
ii  bluez                                     5.53-0ubuntu3.5                       amd64        Bluetooth tools and daemons
ii  bluez-cups                                5.53-0ubuntu3.5                       amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                               5.53-0ubuntu3.5                       amd64        bluez obex daemon
ii  libbluetooth3:amd64                       5.53-0ubuntu3.5                       amd64        Library to use the BlueZ Linux Bluetooth stack
ii  pulseaudio-module-bluetooth               1:13.99.1-1ubuntu3.13                 amd64        Bluetooth module for PulseAudio sound server

```
Also discovered I have no audio capability either, but that is a different issue; however, it may be related.

Advice and suggestions from network subject matter experts willingly accepted.

---

### Post by chili555 on 2022-02-15
May we also see:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

Since you see this: > modinfo: ERROR: Module iwlwifi not found.
I then suspect that the problem is this: [https://askubuntu.com/questions/1350208/wi-fi-does-not-working-in-dell-inspiron-5502-with-ubuntu-20-04/1350354#1350354](https://askubuntu.com/questions/1350208/wi-fi-does-not-working-in-dell-inspiron-5502-with-ubuntu-20-04/1350354#1350354)

---

### Post by him610 on 2022-02-16
@chilli55

Your advice was correct. I had also discovered I simultaneously had a problem with my audio missing which I did solve, and wonder of wonders, it also cured my missing wifi and bluetooth capability:)

Lesson learned - If you suddenly lose audio, wifi, and bluetooth, suspect linux-modules-extra.

I followed advice from 1fallen here [https://ubuntuforums.org/showthread.php?t=2471933]("https://ubuntuforums.org/showthread.php?t=2471933")

Fix is documented here, [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635")

---

