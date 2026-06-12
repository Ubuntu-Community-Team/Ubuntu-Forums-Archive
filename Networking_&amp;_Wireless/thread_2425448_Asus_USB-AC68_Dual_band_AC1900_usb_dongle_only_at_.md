---
title: "Asus USB-AC68 Dual band AC1900 usb dongle only at half speed in ubuntu 19.04"
date: 2019-08-26
forum: Networking &amp; Wireless
---

### Post by edwin22 on 2019-08-26
Hoping to find someone here to help with an issue i have with my asus AC68 usb wifi dongle as this is driving me nuts.
I installed the driver from here:
[https://github.com/zebulon2/rtl8814au](https://github.com/zebulon2/rtl8814au)
i used this one as it has support for kernels newer than 4.19, my kernel is 5.0.0-25-generic

i tested this ac68 with windows 10 and got about 60MB/sec out of it but on ubuntu 19.04 with this driver and kernel i get mostly 25-30ich MB/s

My system info:
ed@nanda:~$ sudo inxi -Fz
System:
  Host: nanda Kernel: 5.0.0-25-generic x86_64 bits: 64 Desktop: Gnome 3.32.2 
  Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP EliteBook 8470p 
  v: A1029C1102 serial: <filter> 
  Mobo: Hewlett-Packard model: 179B v: KBC Version 42.38 serial: <filter> 
  UEFI: Hewlett-Packard v: 68ICF Ver. F.66 date: 09/29/2016 
Battery:
  ID-1: BAT0 charge: 38.0 Wh condition: 38.9/38.9 Wh (100%) 
CPU:
  Topology: Dual Core model: Intel Core i5-3320M bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 1197 MHz min/max: 1200/3300 MHz Core speeds (MHz): 1: 1197 2: 1197 
  3: 1197 4: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
  Display: server: X.Org 1.20.4 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 19.0.8 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.0.0-25-generic 
Network:
  Device-1: Intel 82579LM Gigabit Network driver: e1000e 
  IF: enp0s25 state: down mac: <filter> 
  Device-2: ASUSTek type: USB driver: rtl8814au 
  IF: wlx40b07657e4b3 state: up mac: <filter> 
Drives:
  Local Storage: total: 232.89 GiB used: 175.89 GiB (75.5%) 
  ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 250GB size: 232.89 GiB 
Partition:
  ID-1: / size: 227.74 GiB used: 175.88 GiB (77.2%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 45.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 240 Uptime: 14m Memory: 3.72 GiB used: 2.33 GiB (62.7%) 
  Shell: bash inxi: 3.0.33 
ed@nanda:~$


iwconfig wlx40b07657e4b3
wlx40b07657e4b3  IEEE 802.11AC  ESSID:filter Nickname:"<filter>"
          Mode:Managed  Frequency:5.2 GHz  Access Point: <filter>
          Bit Rate:1.3 Gb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I only get about half of what i get on windows 10 on same machine ( same USB3.0 port too) , i got no clue so far what is causing this huge difference in speed
Did anyone here face this issue before and perhaps can help me out?

---

### Post by scporse on 2020-06-04
I'm facing much the same problem (also with that particular WLAN adapter), although the scenario differs a bit in that I noticed this drop in connection speeds after switching to a [new WLAN driver]("https://github.com/aircrack-ng/rtl8812au") (having previously used the same one as you).
Also, I'm on the slightly older Ubuntu 18.04 LTS.

I have created a post about my issue over [here]("https://ubuntuforums.org/showthread.php?t=2444789&p=13962768#post13962768"), and you're welcome to chime in if you have found out anything new, since you submitted this post.

---

