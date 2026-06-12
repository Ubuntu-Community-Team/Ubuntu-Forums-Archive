---
title: "thinkpad x280 - Kubuntu 18.04 LTS - LTE Modem (4G) not working"
date: 2018-06-10
forum: Networking &amp; Wireless
---

### Post by herrmeier on 2018-06-10
Does anyone have an idea, how i could get the internat LTE (4G)-Modem working?
PLS let me know if there is a working tutorial I just didn't find yet.
Thank your for reading this and giving it a thought,

My provider is: Telefónica Germany GmbH & Co. OHG, here better known as O2 (letter O, number 2)

What did not work so far:
using networkmanager-gui out of the box with its profiles.
mobile broadband
02 surf02
bzw.
02 pinternet.interkom.de
with just any gsm device.

I checked 
usb-modeswitch is already the newest Version (2.5.2+repack0-2ubuntu1).
usb-modeswitch-data is already the newest Version (20170806-2).

[https://wiki.debian.org/Modem/3G](https://wiki.debian.org/Modem/3G)
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

[LIST]
[*]WWAN-LTE-Module
[/LIST]

FIBOCOM L830-EB-00 wwan LTE Modem
[http://www.fibocom.com/prod_view.aspx?TypeId=67&Id=308&FId=t3:67:3](http://www.fibocom.com/prod_view.aspx?TypeId=67&Id=308&FId=t3:67:3)
Manual:
[https://www.endrich.com/fm/2/FIBOCOM_L830-EB-11%20Hardware%20User%20Manual_V1.0.3%281%29.pdf](https://www.endrich.com/fm/2/FIBOCOM_L830-EB-11%20Hardware%20User%20Manual_V1.0.3%281%29.pdf)

```
$ sudo lshw -C communication
*-usb:2                   
       Beschreibung: Kommunikationsgerät
       Produkt: L830-EB-00
       Hersteller: FIBOCOM
       Physische ID: 6
       Bus-Informationen: usb@1:6
       Version: 3.33
       Seriennummer: 0049########000
       Fähigkeiten: usb-2.00
       Konfiguration: driver=cdc_acm maxpower=100mA speed=480Mbit/s

```
[LIST]
[*]general system information:
[/LIST]

```
$ inxi -Fxxxz --no-host
System:    Kernel: 4.15.0-20-generic x86_64 bits: 64 compiler: gcc v: 7.3.0 Desktop: KDE Plasma 5.12.5
           tk: Qt 5.9.5 dm: sddm Distro: Ubuntu 18.04 LTS
Machine:   Type: Laptop System: LENOVO product: 20KF001GGE v: ThinkPad X280 serial: <filter> Chassis: type: 10
           serial: <filter>
           Mobo: LENOVO model: 20KF001GGE v: SDK0J40697 WIN serial: <filter> UEFI [Legacy]: LENOVO
           v: N20ET29W (1.14 ) date: 03/12/2018
Battery:   ID-1: BAT0 charge: 49.9 Wh condition: 49.9/48.0 Wh (104%) volts: 13.0/11.5 model: SMP 01AV471
           type: Li-poly serial: <filter> status: Full cycles: 21
CPU:       Topology: Quad Core model: Intel Core i7-8550U bits: 64 type: MT MCP arch: Kaby Lake rev: A
           L2 cache: 8192 KiB
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31872
           Speed: 1388 MHz min/max: 400/4000 MHz Core speeds (MHz): 1: 1000 2: 1000 3: 1000 4: 1000 5: 1000
           6: 1000 7: 1000 8: 1000
Graphics:  Card-1: Intel UHD Graphics 620 driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:5917
           Display: x11 server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa
           resolution: 1920x1080~60Hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) v: 4.5 Mesa 18.0.0-rc5
           compat-v: 3.0 direct render: Yes
Audio:     Card-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel v: kernel bus ID: 00:1f.3
           chip ID: 8086:9d71
           Sound Server: ALSA v: k4.15.0-20-generic
Network:   Card-1: Intel Ethernet Connection I219-V driver: e1000e v: 3.2.6-k port: N/A bus ID: 00:1f.6
           chip ID: 8086:15d8
           IF: enp0s31f6 state: down mac: <filter>
           Card-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel bus ID: 3b:00.0 chip ID: 8086:24fd
           IF: wlp59s0 state: up mac: <filter>
           IF-ID-1: wwp0s20f0u6 state: down mac: <filter>
Drives:    HDD Total Size: 596.19 GiB used: 220.54 GiB (37.0%)
           ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB512HAJQ-000L7 size: 476.94 GiB speed: 31.6 Gb/s
           lanes: 4 serial: <filter> rev: 4L2QEXA7 scheme: GPT
           ID-2: /dev/sda type: USB vendor: Generic model: SD MMC size: 119.25 GiB serial: <filter> rev: 1.00
           scheme: MBR
Partition: ID-1: / size: 375.79 GiB used: 149.07 GiB (39.7%) fs: ext4 dev: /dev/nvme0n1p6
Sensors:   System Temperatures: cpu: 60.0 C mobo: N/A
           Fan Speeds (RPM): cpu: 0
Info:      Processes: 317 Uptime: 23d 5h 46m Memory: 15.19 GiB used: 7.83 GiB (51.6%) Init: systemd v: 237
           runlevel: 5 Compilers: gcc: 7.3.0 alt: 7 Shell: bash v: 4.4.19 running in: screen inxi: 3.0.11
```

---

### Post by praseodym on 2018-06-10
Lets see
```

lsusb
usb-devices
lsmod
```

---

### Post by herrmeier on 2018-06-10
Hi, I hope that answers your question. Anything else? Thank you for reading it and giving it a thought.
> **praseodym said:**
> Lets see
```

lsusb
usb-devices
lsmod

```

lsusb
[http://paste.ubuntu.com/p/m9F4SPSxBc/](http://paste.ubuntu.com/p/m9F4SPSxBc/)
usb-devices
[http://paste.ubuntu.com/p/FHTh49M9g7/](http://paste.ubuntu.com/p/FHTh49M9g7/)
lsmod
[http://paste.ubuntu.com/p/B4X7M5R6Nh](http://paste.ubuntu.com/p/B4X7M5R6Nh)

---

### Post by user232 on 2018-06-10
I'm curious what inxi -xxx --usb shows, the device is not being correctly detected as a networking device.

---

### Post by praseodym on 2018-06-10
Does the device have a browser interface?

---

### Post by herrmeier on 2018-06-13
> **user232 said:**
> I'm curious what inxi -xxx --usb shows, the device is not being correctly detected as a networking device.
Thank you for your question to post further information. I hope this answers your question. How can I let ubuntu detect the sim card correctly as a networking device?
```
$ inxi -xxx --usb
USB:       Hub: 1:1 usb: 2.0 type: Full speed (or root) hub chip ID: 1d6b:0002 
           Device-1: Logitech Unifying Receiver bus ID: 1:2 usb: 2.0 type: Keyboard chip ID: 046d:c534 
           Device-2: Alcor Micro AU9540 Smartcard Reader bus ID: 1:3 usb: 2.0 type: Chip/SmartCard 
           chip ID: 058f:9540 
           Device-3: Chicony bus ID: 1:6 usb: 2.0 type: Video chip ID: 04f2:b604 
           Device-4: Synaptics bus ID: 1:7 usb: 2.0 type: Vendor Specific Class chip ID: 06cb:009a 
           Device-5: Intel bus ID: 1:10 usb: 2.0 type: Bluetooth chip ID: 8087:0a2b 
           Device-6: N/A bus ID: 1:52 usb: 2.0 type: N/A chip ID: 2cb7:0210 
           Hub: 2:1 usb: 3.0 type: Full speed (or root) hub chip ID: 1d6b:0003 
           Device-7: Realtek bus ID: 2:47 usb: 3.0 type: Mass Storage chip ID: 0bda:0316 
           Hub: 3:1 usb: 2.0 type: Full speed (or root) hub chip ID: 1d6b:0002 
           Hub: 4:1 usb: 3.1 type: Full speed (or root) hub chip ID: 1d6b:0003
```

---

### Post by herrmeier on 2018-06-13
> **praseodym said:**
> Does the device have a browser interface?
Not that I know of.
w/ kind regards

---

