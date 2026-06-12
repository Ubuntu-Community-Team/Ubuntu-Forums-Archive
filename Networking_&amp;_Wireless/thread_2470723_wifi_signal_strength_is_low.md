---
title: "wifi signal strength is low ?"
date: 2022-01-08
forum: Networking &amp; Wireless
---

### Post by brook992 on 2022-01-08
i am having issue with wifi although i am close to router the signal strength is low

[HTML]sudo lshw -C network
[sudo] password for zoro:     
  *-network                 
       description: Ethernet interface
       product: QCA8172 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 20:89:84:ed:6f:46
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:d3500000-d353ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 135
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: c4
       serial: 0c:d2:92:bb:99:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-92-generic firmware=18.168.6.1 ip=192.168.0.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:29 memory:d3400000-d3401fff

[/HTML]
[HTML]iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"TP-Link_CA29"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: E4:C3:2A:AA:CA:29   
          Bit Rate=121.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:13   Missed beacon:0

[/HTML]

[HTML]  Kernel: 5.4.0-92-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Xfce 4.16.0 
           tk: Gtk 3.24.20 wm: xfwm4 dm: LightDM Distro: Linux Mint 20.3 Una 
           base: Ubuntu 20.04 focal 
Machine:   Type: Laptop System: LENOVO product: 20262 v: Lenovo G400s Touch serial: <filter> 
           Chassis: type: 10 v: Lenovo G400s Touch serial: <filter> 
           Mobo: LENOVO model: INVALID v: 31900004Std serial: <filter> UEFI: LENOVO 
           v: 7BCN38WW(V2.04) date: 12/10/2013 
Battery:   ID-1: BAT1 charge: 8.3 Wh condition: 9.1/37.5 Wh (24%) volts: 16.4/14.9 
           model: LENOVO PABAS0241231 serial: <filter> status: Charging 
CPU:       Topology: Dual Core model: Intel Core i5-3230M bits: 64 type: MT MCP arch: Ivy Bridge 
           rev: 9 L2 cache: 3072 KiB 
           flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 20753 
           Speed: 1933 MHz min/max: 1200/3200 MHz Core speeds (MHz): 1: 1694 2: 1642 3: 1869 
           4: 1634 
Graphics:  Device-1: Intel 3rd Gen Core processor Graphics vendor: Lenovo driver: i915 v: kernel 
           bus ID: 00:02.0 chip ID: 8086:0166 
           Device-2: NVIDIA GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] 
           vendor: Lenovo driver: N/A bus ID: 01:00.0 chip ID: 10de:1140 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) v: 4.2 Mesa 21.0.3 
           compat-v: 3.0 direct render: Yes 
Audio:     Device-1: Intel 7 Series/C216 Family High Definition Audio vendor: Lenovo 
           driver: snd_hda_intel v: kernel bus ID: 00:1b.0 chip ID: 8086:1e20 
           Sound Server: ALSA v: k5.4.0-92-generic 
Network:   Device-1: Qualcomm Atheros QCA8172 Fast Ethernet vendor: Lenovo driver: alx v: kernel 
           port: 2000 bus ID: 02:00.0 chip ID: 1969:10a0 
           IF: enp2s0 state: down mac: <filter> 
           Device-2: Intel Centrino Wireless-N 135 driver: iwlwifi v: kernel port: 2000 
           bus ID: 03:00.0 chip ID: 8086:0893 
           IF: wlp3s0 state: up mac: <filter> 
Drives:    Local Storage: total: 465.76 GiB used: 34.18 GiB (7.3%) 
           ID-1: /dev/sda vendor: Western Digital model: WD5000LPVT-24G33T1 size: 465.76 GiB 
           speed: 3.0 Gb/s serial: <filter> 
Partition: ID-1: / size: 456.96 GiB used: 17.09 GiB (3.7%) fs: ext4 dev: /dev/sda2 
USB:       Hub: 1-0:1 info: Full speed (or root) Hub ports: 2 rev: 2.0 chip ID: 1d6b:0002 
           Hub: 1-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 
           chip ID: 8087:0024 
           Device-1: 1-1.3:3 info: Intel type: Bluetooth driver: btusb rev: 2.0 chip ID: 8087:07da 
           Device-2: 1-1.4:4 info: Realtek RTS5129 Card Reader Controller type: <vendor specific> 
           driver: rtsx_usb,rtsx_usb_ms,rtsx_usb_sdmmc rev: 2.0 chip ID: 0bda:0129 
           Hub: 2-0:1 info: Full speed (or root) Hub ports: 2 rev: 2.0 chip ID: 1d6b:0002 
           Hub: 2-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 
           chip ID: 8087:0024 
           Hub: 3-0:1 info: Full speed (or root) Hub ports: 4 rev: 2.0 chip ID: 1d6b:0002 
           Device-3: 3-3:2 info: Elan Micro Touchscreen type: HID driver: hid-multitouch,usbhid 
           rev: 2.0 chip ID: 04f3:016d 
           Device-4: 3-4:3 info: Realtek Lenovo EasyCamera type: Video driver: uvcvideo rev: 2.0 
           chip ID: 0bda:5728 
           Hub: 4-0:1 info: Full speed (or root) Hub ports: 4 rev: 3.0 chip ID: 1d6b:0003 
Sensors:   System Temperatures: cpu: 49.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
           1: deb http: //packages.linuxmint.com una main upstream import backport
           2: deb http: //mirrors.piconets.webwerks.in/ubuntu-mirror/ubuntu focal main restricted universe multiverse
           3: deb http: //mirrors.piconets.webwerks.in/ubuntu-mirror/ubuntu focal-updates main restricted universe multiverse
           4: deb http: //mirrors.piconets.webwerks.in/ubuntu-mirror/ubuntu focal-backports main restricted universe multiverse
           5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           6: deb http: //archive.canonical.com/ubuntu/ focal partner
Info:      Processes: 201 Uptime: 1m Memory: 3.74 GiB used: 659.3 MiB (17.2%) Init: systemd v: 245 
           runlevel: 5 Compilers: gcc: 9.3.0 alt: 9 Client: Unknown python3.8 client inxi: 3.0.38 
[/HTML]

---

### Post by chili555 on 2022-01-09
> Link Quality=[COLOR="#FF0000"]28[/COLOR]/70 I suspect that one of the antenna wires is not snapped firmly into place. Can you check? On most laptops, there is a small door on the bottom that can be opened to see, replace and remove the wireless card.

[IMG]https://www.insidemylaptop.com/images/Asus-K53U-laptop/disassemble-asus-k53u-laptop-24.jpg[/IMG]

---

