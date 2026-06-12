---
title: "? mark on nm-applet"
date: 2018-05-06
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2018-05-06
Hi,

When I boot my PC I see a **[COLOR=#ff0000]?[/COLOR]** mark in place of the nm-applet. It stays like that for about 2-3 minutes and then the connected sign appears.

I am connected directly without a router using Ethernet cable.

Please help me troubleshoot this  issue.

```
$ inxi -Fxd
System:    Host: ubuntu Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: H110M-CS v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 3016 date: 12/27/2016
CPU:       Dual core Intel Core i3-6100 (-MT-MCP-) 
           arch: Skylake-S rev.3 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14784
           clock speeds: max: 3700 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz
Graphics:  Card: Intel HD Graphics 530 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 10 Mbps duplex: full
           mac: 60:45:cb:87:53:a5
Drives:    HDD Total Size: 120.0GB (21.8% used)
           ID-1: /dev/sda model: Samsung_SSD_750 size: 120.0GB
           Optical-1: /dev/sr0 model: HL-DT-ST DVDRAM GH24NSB0
           rev: LN00 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 12x multisession: yes
           audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition: ID-1: / size: 24G used: 5.6G (25%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 84G used: 19G (24%) fs: ext4 dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 213 Uptime: 3:42 Memory: 1866.0/3810.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 


```

---

### Post by linuxyogi on 2018-05-06
[ATTACH=CONFIG]279603[/ATTACH]

^^ This is what is happening.

dmesg

```
[    2.844414] [drm] RC6 on
[    3.055807] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    3.074799] r8169 0000:02:00.0 enp2s0: link down
[    3.074800] r8169 0000:02:00.0 enp2s0: link down
[    3.074896] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.757503] rfkill: input handler disabled
[   16.740686] r8169 0000:02:00.0 enp2s0: link up
[   16.740701] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


```

---

### Post by wildmanne39 on 2018-05-06
Mine does that when my internet goes down but only then.

---

### Post by linuxyogi on 2018-05-06
> **wildmanne39 said:**
> Mine does that when my internet goes down but only then.

My Internet is definitely not down and I can browse the web while the [COLOR=#ff0000]**?**[/COLOR] symbol is displayed.

---

### Post by linuxyogi on 2018-05-06
Did

```
sudo nano  /etc/sysctl.conf 
```

Then added 

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Then reboot. Problem solved.

---

### Post by linuxyogi on 2018-05-06
Sorry. Its not solved. I rebooted and again its stuck on the [COLOR=#ff0000]**?**[/COLOR] symbol

---

