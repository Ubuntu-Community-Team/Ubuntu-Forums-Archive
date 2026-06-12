---
title: "TL WN823N RTL8192EU Reboot vs Shutdown, Wait, Start"
date: 2019-05-29
forum: Networking &amp; Wireless
---

### Post by him610 on 2019-05-29
TL WN823N RTL8192EU - Reboot vs Shutdown-Wait-Start

RE: TP-Link TL WN823N RTL8192EU
Issue: TL WN823N fails to establish wireless connection upon reboot of system

I have owned the referenced USB network adapter for a couple of years now. It is currently connected to a dual-boot machine with Xubuntu 19.04 and 19.10 installed.

Observations over the past several weeks:
Cold Boot: System starts with TL WN823N connecting wirelessly with the router/AP.
Warm Reboot: System starts with TL WN823N NOT connecting with the router/AP.
Shutdown, Wait 30-60 seconds, Boot: System starts with TL WN823N connecting wirelessly with the router/AP.

My best unscientific guess: The warm reboot does not allow time for the registers to drain to 0 volts while the cold boot and the shutdown, wait, boot sequence provides enough time for the registers to drain to 0 volts.

Any thoughts?

```

hugh@x1910:~$ inxi -SMBCN
System:    Host: x1910 Kernel: 5.0.0-15-generic x86_64 bits: 64 Desktop: Xfce 4.13.4 
           Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: <root required> 
           Mobo: ASUSTeK model: AM1I-A v: Rev X.0x serial: <root required> 
           UEFI: American Megatrends v: 0801 date: 03/10/2016 
CPU:       Topology: Quad Core model: AMD Athlon 5350 APU with Radeon R3 bits: 64 type: MCP 
           L2 cache: 2048 KiB 
           Speed: 798 MHz min/max: 800/2050 MHz Core speeds (MHz): 1: 798 2: 798 3: 798 4: 799 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           Device-2: TP-Link TL WN823N RTL8192EU type: USB driver: rtl8xxxu 
hugh@x1910:~$ lsusb | grep WN823N
Bus 001 Device 002: ID 2357:0109 TP-Link TL WN823N RTL8192EU

```
Cold boot and Shutdown, Wait, Start....
```

hugh@x1910:~$ iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlxc025e9194131  IEEE 802.11  ESSID:"cenador"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 10:86:8C:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```
Warm reboot....
```

hugh@x1910:~$ iwconfig
lo        no wireless extensions.

wlxc025e9194131  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enp1s0    no wireless extensions.

```

NO connect wireless-info.txt
[https://paste.ubuntu.com/p/wPYvyWMpMV/]("https://paste.ubuntu.com/p/wPYvyWMpMV/")

Connected wireless-info.txt
[https://paste.ubuntu.com/p/fQrJqWJVwv/]("https://paste.ubuntu.com/p/fQrJqWJVwv/")

Maybe this will help someone else.

---

