---
title: "Please help in setting up wireless security"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by TracyO on 2008-10-11
I have a Netgear WGR614 wireless router.  I had no problems setting it up, but I'd really like to lock my network.  Initially, I used 192.168.1.1, and I arrived at the correct screen.  I tried to do it as a WEP (which was incorrect on my part), I lost my internet, attempted to reset, and have since left my internet unlocked once I got it back.

Every time I try to go back to that page, it doesn't load.  Neither does 192.168.0.1.  I've tried to lock it using Ubuntu network settings, and I can't figure out what I'm doing wrong or not getting.  Can someone please give me instructions?  All I'd like to do is set some kind of WPA for my connection.

Thanks.

---

### Post by jheaton5 on 2008-10-11
You might try this link [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") unless you already have.  No one will be able to help here until you post results of various commands:

```
lshw -C network
```

```
iconfig
```

```
iwconfig
```

```
dmesg | grep -i iwl
```

---

### Post by TracyO on 2008-10-11
> **jheaton5 said:**
> You might try this link [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") unless you already have.  No one will be able to help here until you post results of various commands:

```
lshw -C network
```

tracy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4c:5d:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:22:e2:41
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


```
iconfig
```

tracy-laptop:~$ iconfig
bash: iconfig: command not found
tracy-laptop:~$ iconfig
bash: iconfig: command not found


```
iwconfig
```

tracy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:CD:AF:0E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=87/100  Signal level=-53 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
dmesg | grep -i iwl
```

tracy-laptop:~$ dmesg | grep -i iwl
[   32.104607] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   32.104611] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   32.277480] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.043497] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.051933] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

---

