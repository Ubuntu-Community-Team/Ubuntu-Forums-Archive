---
title: "Network problem in the 15.10"
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by marcio11 on 2016-02-02
Hey folks.


Well, I don't know by where start, but the point is that my ethernet conection its bring me boring, I tryed everything that find and search on web, and nothing help me.
The point is that my Eth0 doesn't appear when I use "ifconfig" this command shows me enp7s0 on the eth0 interface name, and I don't know why, but what but I have 3x "inet6" appearing after my ip address that, have one interesting thing, because doesn't matter what happen, format or reboot, anything, the ip address always gonna be the same.


someone can help me?


Lets show what I tryed to use,
sorry me but I don't know how put in the output command in the boxes, like I saw in another threads.

(always like root)
I use first 

lspci -v

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
    Subsystem: Dell Device 0572
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 2000 [size=256]
    Memory at c1404000 (64-bit, prefetchable) [size=4K]
    Memory at c1400000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 6c-06-00-00-68-4c-e0-00
    Kernel driver in use: r8169


08:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Dell Device 0209
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at c1500000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at c1580000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k

----------------------------------------------------------------------------------------------------------------------------
dmesg | grep r8169

[    1.256373] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.256383] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.257191] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c90000, 90:b1:1c:f6:be:e1, XID 0c900800 IRQ 27
[    1.257194] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.274081] r8169 0000:07:00.0 enp7s0: renamed from eth0
[    3.144286] r8169 0000:07:00.0 enp7s0: link down
[    5.255902] r8169 0000:07:00.0 enp7s0: link up

dmesg | grep ath9k
[    2.842932] ath9k 0000:08:00.0 wlp8s0: renamed from wlan0


--------------------------------------------------------------------------------------------------------------------------
ifconfig 

enp7s0    Link encap:Ethernet  Endereço de HW 90:b1:1c:f6:be:e1  
          inet end.: 192.168.1.42  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::92b1:1cff:fef6:bee1/64 Escope:Link
          endereço inet6: fdf4:22ef:e281:1:../64 Escope:Global
          endereço inet6: fdf4:22ef:e281:1.../64 Escope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:91963 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:64147 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:118743556 (118.7 MB) TX bytes:6760073 (6.7 MB)


lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:65536  Métrica:1
          pacotes RX:1734 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1734 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:161324 (161.3 KB) TX bytes:161324 (161.3 KB)



(my wireless card always turned off, but if I turnOn, its come disconfigured too)

wlp8s0    IEEE 802.11bgn  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thrff   Fragment thrff
          Encryption keyff
          Power Managementff

--------------------------------------------------------------------------------------------------------------------

I don't know why but, something is very wrong.
When I use route -n one route appear and my internet company doesn't know too.

route -n

Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
0.0.0.0         192.168.1.1     0.0.0.0                   UG       100     0        0    enp7s0
**169.254.0.0**     0.0.0.0         255.255.0.0             U         1000   0        0   enp7s0
192.168.1.0     0.0.0.0         255.255.255.0          U        100    0         0   enp7s0

----------------------------------------------------------------------------------------------------------------
my resolv.conf has no dns configurated.
Really, someone could try understand?

cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home

Everybody that I told about doesn't know what happen. They say me "back one version" but doesn't matter what version or distro, has installed, the problem its the same.

---

