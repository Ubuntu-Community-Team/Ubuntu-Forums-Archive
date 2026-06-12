---
title: "Can I fix my WiFi, afterVPN from my university, and network doesnt working by wifi"
date: 2023-02-18
forum: Networking &amp; Wireless
---

### Post by leoxavi3r on 2023-02-18
Hi

Please help?


 I follow these steps from my university to access remote them remote  VPN, but after install successfully (it worked at the moment and I had  full access to PressReader; that was the point), so I restart my  notebook and them my WiFi and Ethernet icons disappear and network stops  work.

 
These are steps (in portuguese) I followed. [https://www.ccuec.unicamp.br/ccuec/material_apoio/tutorial_linux_vpn_18_04](https://www.ccuec.unicamp.br/ccuec/material_apoio/tutorial_linux_vpn_18_04)

 
I fixed the problem with ethernet when I restart Network Manager w/ this command: sudo systemctl restart NetworkManager but WiFi still not works.

 
Do you all can help me to rebuild my original configs?

 
Some more infos

 leo@LeoBook:~$ sudo lshw -C network
  *-network                 
       descrição: Interface sem fio
       produto: BCM4321 802.11a/b/g/n
       fabricante: Broadcom Inc. and subsidiaries
       ID físico: 0
       informações do barramento: pci@0000:02:00.0
       nome lógico: wls4
       versão: 03
       serial: 00:1e:c2:a3:7b:27
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuração: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.50.176 latency=0 multicast=yes wireless=IEEE 802.11
       recursos: irq:16 memória:d0500000-d0503fff memória:d0000000-d00fffff
  *-network
       descrição: Ethernet interface
       produto: 88E8058 PCI-E Gigabit Ethernet Controller
       fabricante: Marvell Technology Group Ltd.
       ID físico: 0
       informações do barramento: pci@0000:03:00.0
       nome lógico: ens5
       versão: 13
       serial: 00:1e:c2:10:9c:8b
       capacidade: 1Gbit/s
       largura: 64 bits
       clock: 33MHz
       capacidades: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuração: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       recursos: irq:27 memória:d0400000-d0403fff porta de E/S:5000(tamanho=256) memória:d0420000-d043ffff
 and this
 leo@LeoBook:~$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 jan 21 17:18 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
leo@LeoBook:~$ sudo dmesg | grep -e e100 -e eno1
[sudo] senha para leo: 
[    0.055034] ACPI: Reserving DSDT table memory at [mem 0xbeee1000-0xbeee55c5]
 and this too
 ip route show
default via 192.168.50.1 dev ens5 proto dhcp metric 100 
default via 192.168.50.1 dev wls4 proto dhcp metric 20600 
169.254.0.0/16 dev wls4 scope link metric 1000 
192.168.50.0/24 dev ens5 proto kernel scope link src 192.168.50.110 metric 100 
192.168.50.0/24 dev wls4 proto kernel scope link src 192.168.50.176 metric 600 

this
ping -c 5 192.168.50.176
PING 192.168.50.176 (192.168.50.176) 56(84) bytes of data.
64 bytes from 192.168.50.176: icmp_seq=1 ttl=64 time=0.116 ms
64 bytes from 192.168.50.176: icmp_seq=2 ttl=64 time=0.123 ms
64 bytes from 192.168.50.176: icmp_seq=3 ttl=64 time=0.080 ms
64 bytes from 192.168.50.176: icmp_seq=4 ttl=64 time=0.110 ms
64 bytes from 192.168.50.176: icmp_seq=5 ttl=64 time=0.079 ms

--- 192.168.50.176 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4094ms
rtt min/avg/max/mdev = 0.079/0.101/0.123/0.018 ms


this seems work but i still connected by ethernet (cable)

 
when i disconnect cable, appears a ? in front of wifi icon and network doesn't work in apps or browsers

 
Please help me get out of this trouble Cause its carnival here in Brazil and no support from university

 
Thanks

 
Leo

 sudo systemctl restart NetworkManager

 another options / tips please

---

### Post by grahammechanical on 2023-02-19
> when i disconnect cable, appears a ? in front of wifi icon and network doesn't work in apps or browsers

That indicates that the WiFi adapter is not connecting to the hub/router or the hub/router is not connecting to the Internet Service Provider (ISP)

> configuração: broadcast=yes driver=wl0 driverversion=6.30.223.271  (r587334) ip=192.168.50.176 latency=0 multicast=yes wireless=IEEE 802.11

This indicates that a WiFi driver is installed and working.

If you can connect to the internet through ethernet then the hub/router is connected to the ISP. Check the router/hub antenna. Are they pointing a direction that will give a good signal to the WiFi adapter?

Regards

---

### Post by leoxavi3r on 2023-02-19
Hi,

> **grahammechanical said:**
> That indicates that the WiFi adapter is not connecting to the hub/router or the hub/router is not connecting to the Internet Service Provider (ISP)

This message gave me an idea: I connected a Ralink RT2870/RT3070 WiFi adapter to my notebook and worked, automatically. But I really want to get back my Broadcom and subsidiaries BCM4321, original from notebook (it's an old black MacBook late-08 with Ubuntu 22.04 installed). What can I do to reconnect this WiFi driver to normality?


> **grahammechanical said:**
> 
This indicates that a WiFi driver is installed and working.


Maybe with some error, because after I installed VPN from my university, according to my original text (link with all instructions that I followed), I can't use network anymore. One more thing: always I restart my notebook, WiFi icon disappear and I have to type the command ```
sudo systemctl restart NetworkManager
``` at terminal.

> 
If you can connect to the internet through ethernet then the hub/router is connected to the ISP. Check the router/hub antenna. Are they pointing a direction that will give a good signal to the WiFi adapter?
Regards

The router/rub antenna ins't the problem, because my SmarTV's fine and w/ USB adapter, that I mentioned before, the same internet network works. So I'm supposing that is some config or command that vpn install "broke"

more help

---

### Post by leoxavi3r on 2023-02-20
up

---

### Post by leoxavi3r on 2023-03-06
up2 help

---

