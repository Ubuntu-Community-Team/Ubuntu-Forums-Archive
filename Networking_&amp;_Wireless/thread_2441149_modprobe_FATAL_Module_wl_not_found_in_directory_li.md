---
title: "modprobe: FATAL: Module wl not found in directory /lib/modules/5.4.0-24-lowlatency"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by saikat0511 on 2020-04-20
I installed **kubuntu 20.04** and cannot get my wifi to work. My laptop uses **BCM43142** adapter and as usual I installed the ***bcmwl-kernel-source*** package. 
The install process completed successfully but their was an fatal error(mentioned in the title) in the process. I restarted my system and wifi still didn't worked. I did a manual modprobe wl and it still can't be found. My kernel version is **5.4.0-24-lowlatency**(default in kubuntu 20.04). Is the broadcom driver incompatible for this kernel?

---

### Post by ActionParsnip on 2020-04-21
Are there any bugs reported?
Is it OK with the "-generic" kernel (I assume you are someone who makes music on their system to use the "-lowlatency" kernel)

---

### Post by deadflowr on 2020-04-21
Posted here is reference to a bug about nvidia pulling in the lowlatency kernel:
[https://discourse.ubuntu.com/t/20-04-release-candidate-isos-ready-for-testing/15406/10]("https://discourse.ubuntu.com/t/20-04-release-candidate-isos-ready-for-testing/15406/10")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873867]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873867")
If no nvidia driver getting installed, I wonder if the same thing happens with other restricted drivers like the bcmwl-kernel-source package.

---

### Post by slickymaster on 2020-04-21
*Thread moved to **Networking & Wireless**.*

---

### Post by #&amp;thj^% on 2020-04-21
> **deadflowr said:**
> Posted here is reference to a bug about nvidia pulling in the lowlatency kernel:
[https://discourse.ubuntu.com/t/20-04-release-candidate-isos-ready-for-testing/15406/10]("https://discourse.ubuntu.com/t/20-04-release-candidate-isos-ready-for-testing/15406/10")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873867]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873867")
If no nvidia driver getting installed, I wonder if the same thing happens with other restricted drivers like the bcmwl-kernel-source package.

Thanks for the link deadflowr, They are working on fix now at the time writing this, the problem was pointing to, that apt install nvidia will always select some lrm provider but not necessarily the one that matches your kernel.
> (failing to install lowlatency).
Mine is fine W/O Nvidia.
```
sudo inxi -Fx
System:
  Host: me-ThinkPad-T430 Kernel: 5.4.0-26-lowlatency x86_64 bits: 64 
  compiler: gcc v: 9.3.0 Desktop: MATE 1.24.0 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 2349M88 v: ThinkPad T430 
  serial: PBNWETV 
  Mobo: LENOVO model: 2349M88 serial: 1ZLMB27S67W UEFI [Legacy]: LENOVO 
  v: G1ETB8WW (2.78 ) date: 09/19/2018 
Battery:
  ID-1: BAT0 charge: 49.4 Wh condition: 52.2/56.2 Wh (93%) 
  model: LGC 45N1005 status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core i5-3320M bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 3072 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 20752 
  Speed: 1198 MHz min/max: 1200/3300 MHz Core speeds (MHz): 1: 1197 2: 1198 
  3: 1197 4: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2) 
  v: 4.2 Mesa 20.0.4 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio vendor: Lenovo 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-26-lowlatency 
Network:
  Device-1: Intel 82579LM Gigabit Network vendor: Lenovo driver: e1000e 
  v: 3.2.6-k port: 6080 bus ID: 00:19.0 
  IF: enp0s25 state: down mac: 00:21:cc:c3:71:70 
  Device-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi 
  v: kernel port: efa0 bus ID: 03:00.0 
  IF: wlp3s0 state: up mac: 60:67:20:42:b6:0c 
  IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 167.68 GiB used: 8.64 GiB (5.2%) 
  ID-1: /dev/sda vendor: Intel model: SSDSC2BW180A3L size: 167.68 GiB 
Partition:
  ID-1: / size: 164.05 GiB used: 8.64 GiB (5.3%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: 0.0 C 
  Fan Speeds (RPM): cpu: 2552 
Info:
  Processes: 224 Uptime: 4m Memory: 11.39 GiB used: 683.5 MiB (5.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 
  inxi: 3.0.38 

```

---

