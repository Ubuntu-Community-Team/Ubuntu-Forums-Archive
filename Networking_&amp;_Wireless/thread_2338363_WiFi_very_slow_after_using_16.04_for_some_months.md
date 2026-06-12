---
title: "WiFi very slow after using 16.04 for some months"
date: 2016-09-27
forum: Networking &amp; Wireless
---

### Post by robertocsp on 2016-09-27
Hi! I've installed Ubuntu LTS 16.04 in HP notebook dm4 and after some months using it and installing lots of softwares, WiFi connection began to be very slow.
roberto@roberto-HP--Note:~$ sudo lshw -C network
  *-network               
       descrição: Ethernet interface
       produto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       ID físico: 0
       informações do barramento: pci@0000:02:00.0
       nome lógico: enp2s0
       versão: 03
       serial: 64:31:50:9c:db:f9
       tamanho: 10Mbit/s
       capacidade: 1Gbit/s
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:26 porta de E/S:2000(tamanho=256) memória:c0404000-c0404fff memória:c0400000-c0403fff
  *-network
       descrição: Interface sem fio
       produto: Centrino Wireless-N 1000 [Condor Peak]
       fabricante: Intel Corporation
       ID físico: 0
       informações do barramento: pci@0000:03:00.0
       nome lógico: wlp3s0
       versão: 00
       serial: 8c:a9:82:96:1d:00
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=iwlwifi driverversion=4.4.0-38-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:29 memória:c2400000-c2401fff
roberto@roberto-HP--Note:~$ 

If I connect a network cable it works normally.
Any idea to solve this problem?

---

