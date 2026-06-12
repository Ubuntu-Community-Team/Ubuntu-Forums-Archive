---
title: "No Bluetooth in Ubuntu 12.04 using Dell Inspirion e1505"
date: 2016-11-17
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2016-11-17
I'm running Ubuntu 12.04 on a Dell Inspirion e1505.

It supposedly has Bluetooth capability but I can't figure out how to activate it.  Fn- F2 keys only turn WiFi off.

The Bluetooth option in System Settings doesn't indicate my Bluetooth headphones are attached/connected.  No, they don't work regardless of what I see on the settings.

Any idea how to fix this?

Thanks

---

### Post by PDA1 on 2016-11-17
Here's some, maybe, useful information;

```
   ##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 003: ID 046d:c534 Logitech, Inc. 

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
iwl3945                73186  0 
iwl_legacy             71334  1 iwl3945
mac80211              444736  2 iwl3945,iwl_legacy
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211
ssb                    50691  1 b44
wmi                    18744  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9854342 (9.8 MB)  TX bytes:1504566 (1.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WXC2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'WXC2' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:93   Missed beacon:0
```

---

### Post by jeremy31 on 2016-11-18
I do not see anything in your results that would indicate bluetooth hardware being present

---

