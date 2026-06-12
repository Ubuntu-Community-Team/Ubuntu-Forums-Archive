---
title: "No ethernet or wifi in Ubuntu 16.04 fresh install"
date: 2018-03-05
forum: Networking &amp; Wireless
---

### Post by lezorich on 2018-03-05
Hi everyone,

For work I have a new HP Omen laptop. I just installed Ubuntu 16.04 on it but I can't get internet to work, either ethernet or wifi. I have searched all day, but haven't been able to fix the issue. Do you know what can be going on? Is like the ethernet cable is not being recognized by the system.

```
lshw -C network
``` throws this:

```

  *-network               
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: enp3s0
       versión: 16
       serie: 48:ba:4e:41:03:49
       tamaño: 10Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       recursos: irq:23 ioport:c000(size=256) memoria:dfd04000-dfd04fff memoria:dfd00000-dfd03fff
  *-network NO RECLAMADO
       descripción: Network controller
       producto: Realtek Semiconductor Co., Ltd.
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:04:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress cap_list
       configuración: latency=0
       recursos: ioport:b000(size=256) memoria:dfc00000-dfc0ffff

```

```
lspci -nnk | grep -iA2 eth
``` prints this:

```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 16)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:838f]
	Kernel driver in use: r8168
	Kernel modules: r8168

```

```
ifconfig -a
```:

```

enp3s0    Link encap:Ethernet  direcciónHW 48:ba:4e:41:03:49  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:23 Dirección base: 0x1000 


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:4404 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4404 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:334640 (334.6 KB)  TX bytes:334640 (334.6 KB)

```

and ```
cat /etc/network/interfaces
```:

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface enp3s0 inet dhcp

```

Thanks!

---

### Post by chili555 on 2018-03-05
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface enp3s0 inet dhcp
```Please amend the file to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet dhcp
```Then, from the terminal:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```Any improvement?

---

