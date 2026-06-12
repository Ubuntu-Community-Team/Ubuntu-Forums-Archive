---
title: "Realtek Wireless Adapter is not recognized"
date: 2024-01-16
forum: Networking &amp; Wireless
---

### Post by kellyss14 on 2024-01-16
Hello, I am new to ubuntu and got hindered by an issue with some old equipment. At first, my wifi adapter was kinda half-working: it could see the networks around and attempt to connect, only to say Connection Failed (even when connecting to passwordless spots). Then I updated drivers automatically after installation and it just completely disappeared, system no longer sees any wifi adapter being present at all.

I cannot find a linux driver for this one to try to download it manually either, maybe I am just looking not good enough?

Realtek RTL8191SU Wireless lan 802.11n USB 2.0 Network Adapter - full name.

Thanks in advance, I really cannot do much until it is solved. Right now all I can do is establishing a temporary connection via mobile usb.

---

### Post by readableauthor on 2024-01-16
Please post more system info. Run in terminal
```

sudo apt install inxi
inxi -Fxxzc0 in terminal                                  

```

---

### Post by kellyss14 on 2024-01-16
Without any visible reason, it stopped recognizing my phone usb internet modem either (it was working correctly last time). Feels like some drivers just disappeared(?) after update altogether. Can't even download from the machine directly anymore. Please advise.

Note: lsusb command properly shows usb equipment. IMC Network Mediao 802.11n WLAN [Realtek RTL8191SU] and Samsung phone with (tethering mode). It just receives no internet connection whatsoever.

Maybe I can reinstall network drivers manually from usb or something?

---

### Post by kellyss14 on 2024-01-16
To add: on "Advanced options for Ubuntu" on the boot after update I have -with Linux 5.15.0-91-generic and older 5.15.0-67-generic.

The older version still recognizes the usb tethering and I was able to run the requested code. It shows:

System:
  Kernel: 5.15.0-67-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: MEDION model: H77H2-EM v: V1.0 
  serial: <filter> BIOS: American Megatrends v: EM0411-M8 
  date: 04/11/2012 
CPU:
  Topology: Quad Core model: Intel Core i7-3770 bits: 64 
  type: MT MCP arch: Ivy Bridge rev: 9 L2 cache: 8192 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 
  vmx 
  bogomips: 54273 
  Speed: 1597 MHz min/max: 1600/3900 MHz 
  Core speeds (MHz): 1: 1596 2: 1680 3: 1886 4: 1626 
  5: 1596 6: 1597 7: 1597 8: 1597 
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050 Ti] 
  vendor: PNY driver: N/A bus ID: 01:00.0 
  chip ID: 10de:1c82 
  Display: x11 server: X.Org 1.20.13 
  driver: fbdev,nouveau unloaded: modesetting,vesa 
  compositor: gnome-shell resolution: 640x480~73Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) 
  v: 4.5 Mesa 21.2.6 compat-v: 3.1 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition 
  Audio 
  vendor: Elite Systems driver: snd_hda_intel v: kernel 
  bus ID: 00:1b.0 chip ID: 8086:1e20 
  Device-2: NVIDIA GP107GL High Definition Audio 
  vendor: PNY driver: snd_hda_intel v: kernel 
  bus ID: 01:00.1 chip ID: 10de:0fb9 
  Sound Server: ALSA v: k5.15.0-67-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit 
  Ethernet 
  vendor: Elite Systems driver: r8169 v: kernel 
  port: d000 bus ID: 03:00.0 chip ID: 10ec:8168 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: IMC Networks Mediao 802.11n WLAN [Realtek 
  RTL8191SU] 
  type: USB driver: r8712u bus ID: 2-1.7:4 
  chip ID: 13d3:3306 
  IF: wlx94dbc97896de state: down mac: <filter> 
  IF-ID-1: usb0 state: unknown speed: -1 duplex: half 
  mac: <filter> 
Drives:
  Local Storage: total: 2.05 TiB used: 10.99 GiB (0.5%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB 
  size: 232.89 GiB speed: 6.0 Gb/s serial: <filter> 
  ID-2: /dev/sdb vendor: Seagate 
  model: ST2000DM001-1CH164 size: 1.82 TiB 
  speed: 3.0 Gb/s serial: <filter> temp: 33 C 
Partition:
  ID-1: / size: 771.20 GiB used: 10.99 GiB (1.4%) 
  fs: ext4 dev: /dev/sdb6 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 254 Uptime: 3m Memory: 15.59 GiB 
  used: 905.9 MiB (5.7%) Init: systemd v: 245 runlevel: 5 
  Compilers: gcc: N/A Shell: bash v: 5.0.17 
  running in: gnome-terminal inxi: 3.0.38



Note that it also again like the first time recognizes the wifi adapter, it again detects hotspots but cannot connect to them. 
My iso was installed from the official ubuntu site, should not be botched.

---

### Post by dolanor on 2024-01-25
I have the same issue. Tethering stopped working in **linux-image-5.15.0-91-generic** and **linux-image-5.15.0-92-generic**.

I have a Samsung Galaxy S21.
On **linux-image-5.15.0-88-generic** it was **fine**.

What is missing from **dmesg** in linux-image-5.15.0-91-generic

```
[  836.834312] usb 1-6: new high-speed USB device number 10 using xhci_hcd
[  836.987699] usb 1-6: New USB device found, idVendor=04e8, idProduct=6860, bcdDevice= 5.04
[  836.987720] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  836.987731] usb 1-6: Product: SAMSUNG_Android
[  836.987738] usb 1-6: Manufacturer: SAMSUNG
[  836.987746] usb 1-6: SerialNumber: XXX
[  837.050831] cdc_acm 1-6:1.1: ttyACM0: USB ACM device
[  837.050888] usbcore: registered new interface driver cdc_acm
[  837.050889] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[  851.714136] usb 1-6: USB disconnect, device number 10
[  852.201875] usb 1-6: new high-speed USB device number 11 using xhci_hcd
[  852.351707] usb 1-6: New USB device found, idVendor=04e8, idProduct=6863, bcdDevice= 5.04
[  852.351728] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  852.351740] usb 1-6: Product: SAMSUNG_Android
[  852.351748] usb 1-6: Manufacturer: SAMSUNG
[  852.351756] usb 1-6: SerialNumber: XXX
[  852.356801] rndis_host 1-6:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-6, RNDIS device, 3e:57:cf:9b:51:ea
```

---

