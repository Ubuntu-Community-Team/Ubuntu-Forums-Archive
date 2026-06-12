---
title: "Wifi connection runs slowly"
date: 2016-02-25
forum: Networking &amp; Wireless
---

### Post by david-palop on 2016-02-25
Hello,

I bought a new netbook (Vant Moove Mini) with ubuntu 14.04 and the wifi connection is very slow when I be at few meters from the router.
Nearly the router the signal is normal.

Other displays run correctly at the same distance (ipad, cellular phones, other netbooks, etc.) and the issue it's the same in others wifi networks.

Also the wifi connection turns-off in a few minutes of slow connection.

Can you help me to find a solution, please?

Thank you.

---

### Post by kc1di on 2016-02-25
Hello david-palop  and Welcome to Ubuntu,

We need a little more information to be of help. need to know what wireless card is in your machine. 
If you don't know what the card is go to a terminal and type ```
lshw -C network
```
and post the results here.

---

### Post by david-palop on 2016-02-25
thanks for your reply kc1di, the output is the next:

```

  *-network               
       descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0.2
       información del bus: pci@0000:01:00.2
       nombre lógico: eth0
       versión: 06
       serie: 80:fa:5b:22:a3:f1
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8402-1_0.0.1 10/26/11 ip=192.168.0.157 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:118 ioport:e000(size=256) memoria:81310000-81310fff memoria:a0000000-a0003fff
  *-network
       descripción: Interfaz inalámbrica
       producto: Wireless 7265
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlan0
       versión: 61
       serie: 60:57:18:ec:6a:d5
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwlwifi driverversion=4.4.0-040400-generic firmware=25.30.13.0 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:121 memoria:81200000-81201fff


```

---

### Post by kc1di on 2016-02-27
Hi Sorry it took so long to get back to you.  Been busy here. 
There is a problem with the driver for the dual channel chipset you have.  
you can try this command in a terminal it may fix the problem.
```
sudo sh -c 'echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf'
``` It will ask you for your password.

Good luck.

---

### Post by david-palop on 2016-03-02
Thank you for your reply, kc1di,

I tried your commands, but it runs already slowly.
They is something that I can try to fix the problem?

Thank you!

---

