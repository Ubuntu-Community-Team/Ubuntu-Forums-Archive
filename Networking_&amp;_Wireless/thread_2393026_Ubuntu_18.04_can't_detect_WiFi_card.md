---
title: "Ubuntu 18.04 can't detect WiFi card"
date: 2018-05-28
forum: Networking &amp; Wireless
---

### Post by stii on 2018-05-28
The title says it all! I have just installed Ubuntu 18.04 and it doesn't show WiFi options at all in the network menu. inxi and lspci can't detect WiFi card. Linux Mint 18.3 was previously installed on this PC and WiFi card was being detected and WiFi worked fine. Before Linux Mint, Windows 7 Starter was installed and everything worked fine too.

Here is the info that inxi -b gives

```
System:    Host: dragana-1000H Kernel: 4.15.0-22-generic i686 bits: 32
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: ASUSTeK product: 1000H v: x.x serial: N/A
           Mobo: ASUSTeK model: 1000H v: x.xx serial: N/A
           BIOS: American Megatrends v: 2204 date: 10/21/2009
Battery    BAT0: charge: 35.2 Wh 78.6% condition: 44.8/55.3 Wh (81%)
CPU:       Single core Intel Atom N270 (-MT-) speed/max: 866/1600 MHz
Graphics:  Card: Intel Mobile 945GSE Express Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 )
           drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1024x600@60.00hz
           OpenGL: renderer: Mesa DRI Intel 945GME x86/MMX/SSE2
           version: 1.4 Mesa 18.0.0-rc5
Network:   Card: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E
Drives:    HDD Total Size: 160.0GB (3.6% used)
Info:      Processes: 135 Uptime: 31 min Memory: 239.1/2003.9MB
           Client: Shell (bash) inxi: 2.3.56

```
Anyone has an idea what can I try?

---

### Post by jeremy31 on 2018-05-28
*Thread moved to **Networking & Wireless**.*

---

### Post by stii on 2018-05-29
Nevermind, I figured it out. Somehow, WLAN card, Bluetooth and some other things got disabled in BIOS. I have no idea how.

---

