---
title: "Newbie: 20.04 LTS Wifi drops"
date: 2020-08-09
forum: Networking &amp; Wireless
---

### Post by josephtj on 2020-08-09
Hi

My wifi gets disconnected in the first instance of trying "arping changing time to 15 mins, setting wifi.powesave=2" in 1 hour and thereafter every 20 mins. Issue crops up when using Google Meet or Zoom for attending classes. I have tried many of the available fixes like using WICD, editing firmware, arping changing time to 15 mins, setting wifi.powesave=2, removing backport-iwlwifi-dkms.
Error : Unavailable -802.1x supplicant failed
If I am using Youtube or do general browsing the issue does not crop up. Pls help.
Laptop : Asus K50IJ
[B]
inxi -Fzx [/B]result
System:
  Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: ASUSTeK product: K50IJ v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: K50IJ v: 1.0 serial: <filter> 
  BIOS: American Megatrends v: 213 date: 09/09/2009 
CPU:
  Topology: Dual Core model: Intel Core2 Duo T6600 bits: 64 type: MCP 
  arch: Penryn rev: A L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 bogomips: 8777 
  Speed: 1197 MHz min/max: 1200/2200 MHz Core speeds (MHz): 1: 1197 2: 1197 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: ASUSTeK 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: intel 
  unloaded: fbdev,modesetting,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Santa Cruz Operation 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-42-generic 
Network:
  Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter 
  vendor: AzureWave AW-NE785 / AW-NE785H 802.11bgn driver: ath9k v: kernel 
  port: c400 bus ID: 02:00.0 
  IF: wlan0 state: up mac: <filter> 
  Device-2: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet 
  vendor: ASUSTeK driver: ATL1E v: N/A port: ec00 bus ID: 03:00.0 
  IF: eth0 state: down mac: <filter> 
Drives:
  Local Storage: total: 298.09 GiB used: 25.53 GiB (8.6%) 
  ID-1: /dev/sda vendor: Seagate model: ST9320325AS size: 298.09 GiB 
  temp: 40 C 
Partition:
  ID-1: / size: 30.95 GiB used: 25.53 GiB (82.5%) fs: ext4 dev: /dev/sda9 
  ID-2: swap-1 size: 4.21 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 49.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 226 Uptime: 52m Memory: 3.81 GiB used: 1.00 GiB (26.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 

**iwconfig **result
eth0      no wireless extensions.


wlan0     IEEE 802.11  ESSID:"Nokia 7.1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 22:6A:64:3B:FC:22   
          Bit Rate=58.5 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:114   Missed beacon:0


lo        no wireless extensions.

**sudo nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf**
[connection]
wifi.powersave = 2

---

