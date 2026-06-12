---
title: "Network ACtivation failed"
date: 2020-03-24
forum: Networking &amp; Wireless
---

### Post by kiko19 on 2020-03-24
hi i am new to the OS Ubuntu
i have a weird problem... i can connect to my wifinetwork but then it shows an '?' or '...' and then activation failed to connect or something like that!!
i really need help!
i wrote nmcli: [HTML]wlo1: ligado to NOS-0DA1
        "Realtek Sunrise Point-LP PCI Express Root Port"
        wifi (rtl8723de), DC:F5:05:2D:0E:5D, hw, mtu 1500
        ip4 default
        inet4 192.168.1.11/24
        route4 0.0.0.0/0
        route4 192.168.1.0/24
        route4 169.254.0.0/16
        inet6 fe80::19cb:7cad:e177:4feb/64
        route6 ff00::/8
        route6 fe80::/64
        route6 fe80::/64
[/HTML]

ifconfig: [HTML]
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether b0:0c:d1:ea:f0:2c  txqueuelen 1000  (Ethernet)
        RX packets 14322  bytes 11705527 (11.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11048  bytes 1460377 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 129  base 0x9000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Loopback Local)
        RX packets 6066  bytes 526874 (526.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6066  bytes 526874 (526.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.11  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::19cb:7cad:e177:4feb  prefixlen 64  scopeid 0x20<link>
        ether dc:f5:05:2d:0e:5d  txqueuelen 1000  (Ethernet)
        RX packets 5238  bytes 2965763 (2.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3988  bytes 908796 (908.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
[/HTML]
sudo lshw -C network: [HTML]
 *-network                 
       descrição: Ethernet interface
       produto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       ID físico: 0
       informações do barramento: pci@0000:02:00.0
       nome lógico: eno1
       versão: 15
       serial: b0:0c:d1:ea:f0:2c
       tamanho: 10Mbit/s
       capacidade: 1Gbit/s
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       recursos: irq:129 porta de E/S:4000(tamanho=256) memória:a4204000-a4204fff memória:a4200000-a4203fff
  *-network
       descrição: Interface sem fio
       produto: Realtek Semiconductor Co., Ltd.
       fabricante: Realtek Semiconductor Co., Ltd.
       ID físico: 0
       informações do barramento: pci@0000:03:00.0
       nome lógico: wlo1
       versão: 00
       serial: dc:f5:05:2d:0e:5d
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=rtl8723de driverversion=5.3.0-40-generic firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       recursos: irq:141 porta de E/S:3000(tamanho=256) memória:a4100000-a410ffff
[/HTML]

---

### Post by praseodym on 2020-03-25
SecureBoot is disabled?

---

### Post by HansCombee on 2020-03-26
You seem to be having a valid IP address, what happend if you type "ping www.google.com"

---

