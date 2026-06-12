---
title: "RTL8723BE: Wifi always disocnecting and can't connect again and must be restarted to"
date: 2017-05-28
forum: Networking &amp; Wireless
---

### Post by rofifathurrohman on 2017-05-28
[COLOR=#242729][FONT=Arial]i'm frustating with my new laptop, Wifi works well and can detect wifi signal around it. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem is when i connected to my wifi just 1-2 minutes the wifi will be disconnecting and when i try to reconnect, wifi doesn't to connect.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After restarting the laptop, all work as usual again, I can connect and again only 1-2 minutes wifi will be disconnected.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have tried kali linux, ubuntu, opensuse it still same. Now, my laptop is using Elementary OS and Realtek RTL8723BE PCIe Wireless Network Adapter[/FONT][/COLOR]

> test@test:~$ inxi -Fxz
System:    Host: hmvoc9 Kernel: 4.8.0-52-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Gnome  (Gtk 3.18.9-1ubuntu3.3) Distro: elementary 0.4.1 loki
Machine:   System: LENOVO (portable) product: 80KY v: Lenovo G40-80
           Mobo: LENOVO model: Lenovo G40-80 v: NO DPK Bios: LENOVO v: B0CN80WW date: 05/18/2015
CPU:       Dual core Intel Core i3-4030U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7581
           clock speeds: max: 1800 MHz 1: 799 MHz 2: 799 MHz 3: 809 MHz 4: 830 MHz
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0
           Card-2: Advanced Micro Devices [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
           bus-ID: 04:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 12.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-52-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 5000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter driver: rtl8723be bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (2.4% used) ID-1: /dev/sda model: WDC_WD5000LPCX size: 500.1GB
Partition: ID-1: / size: 23G used: 3.7G (18%) fs: ext4 dev: /dev/sda9
           ID-2: /home size: 74G used: 129M (1%) fs: ext4 dev: /dev/sda8
           ID-3: swap-1 size: 8.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda7
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 45.0C mobo: N/A gpu: 42.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 199 Uptime: 19 min Memory: 1043.6/3871.3MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

[COLOR=#242729][FONT=Arial]
iwconfig
[/FONT][/COLOR]
> test@test:~$ iwconfig
lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

enp0s20u3  no wireless extensions.

enp2s0    no wireless extensions.

[COLOR=#242729][FONT=Arial]Wireless Script

[Here]("https://pastebin.com/15wETwA8")

Note: When i check my info, I'm using mobile connection with usb tether.[/FONT][/COLOR]

---

### Post by Hadaka on 2017-05-28
Hi please open a terminal then copy and paste one line at a time..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
then do..```
sudo iw reg set ID
sudo sed -i 's/=.*/=ID/' /etc/default/crda
```
boot and test wireless

You currently have your ant sel set to 2, If it drops when you move away from the router
try setting it to 1

# to set ant_sel=1
```
sudo sed -i 's/=2/=1/' /etc/modprobe.d/rtl8723beant.conf
```

# to set ant_sel=2
```
sudo sed -i 's/=1/=2/' /etc/modprobe.d/rtl8723beant.conf
```

thanks.

---

