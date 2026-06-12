---
title: "[ubuntu] Realtek RTL8111/8168/8411 PCIE with Ubuntu 18.04.4 LTS Wi-Fi cannot work"
date: 2021-05-15
forum: Networking &amp; Wireless
---

### Post by sirdmon on 2021-05-15
On a brand new HP Pavilion Gaming Laptop 16-a0xxx on Ubuntu Mate 18.04.04 Wi-Fi is not working

```
inxi -Fxz

System:    Host: hp Kernel: 5.4.0-73-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: MATE 1.20.1 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: laptop System: HP product: HP Pavilion Gaming Laptop 16-a0xxx serial: N/A
           Mobo: HP model: 87AE v: 32.31 serial: N/A
           UEFI: AMI v: F.20 date: 11/04/2020
Battery    BAT0: charge: 6.7 Wh 13.4% condition: 50.2/50.2 Wh (100%)
           model: HP Primary status: Discharging
CPU:       6 core Intel Core i7-10750H (-MT-MCP-) arch: N/A cache: 12288 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 31199
           clock speeds: max: 5000 MHz 1: 1065 MHz 2: 2277 MHz 3: 1745 MHz
           4: 2086 MHz 5: 2215 MHz 6: 2055 MHz 7: 2019 MHz 8: 2022 MHz
           9: 1866 MHz 10: 1714 MHz 11: 1950 MHz 12: 1687 MHz
Graphics:  Card-1: Intel Device 9bc4 bus-ID: 00:02.0
           Card-2: NVIDIA Device 1f95 bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.01hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics (Comet Lake 3x8 GT2)
           version: 4.5 Mesa 19.2.8 Direct Render: Yes
Audio:     Card-1 NVIDIA Device 10fa driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel Device 06c8 driver: sof-audio-pci bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k5.4.0-73-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8168 v: 8.045.08-NAPI port: 4000 bus-ID: 03:00.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Realtek Device c822
           driver: rtw_pci port: 3000 bus-ID: 04:00.0
           IF: wlo1 state: down mac: <filter>
Drives:    HDD Total Size: 512.1GB (1.3% used)
           ID-1: /dev/nvme0n1 model: SAMSUNG_MZVLQ512HALU size: 512.1GB
Partition: ID-1: / size: 467G used: 5.2G (2%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 705M used: 232M (36%)
           fs: ext4 dev: /dev/nvme0n1p2
           ID-3: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A gpu: 38.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 297 Uptime: 2 min Memory: 566.6/15783.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
```

I have Secure Boot disabled

Installing r8168-dkms driver instead of r8169 did not worked for me [URL="https://askubuntu.com/questions/1308793/realtek-r8169-driver-ubuntu-20-04-with-rtl8111-8168-8411-pci-express-gigabit-et"]https://askubuntu.com/questions/1308793/realtek-r8169-driver-ubuntu-20-04-with-rtl8111-8168-8411-pci-express-gigabit-et
[/URL]
Any hint / idea would be helpful

---

### Post by jeremy31 on 2021-05-15
It shows you have a driver, post results for ```
rfkill list
```

---

### Post by sirdmon on 2021-05-15
```
rfkill list
```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by sirdmon on 2021-05-15
Solved by upgrading the distro to Ubuntu 20.04.2 LTS

---

