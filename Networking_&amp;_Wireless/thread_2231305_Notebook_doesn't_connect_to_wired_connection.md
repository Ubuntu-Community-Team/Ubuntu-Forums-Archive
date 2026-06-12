---
title: "Notebook doesn't connect to wired connection"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by dylan0005 on 2014-06-24
Hi everyone! Mi Pc info: ASUSPCeeepc series 900, 4 GB HDD, 2 GB RAM- OS: Ubuntu 12.04 lts 

Well, my notebook (just 1 day ago ) doesn't connect to wired connection. When I plug in the network wire, the Network status says: "Wired connection 1 disconnected" & it doesn't connect the whole time until I turn off the notebook.

I've tried if it connect with others distros like lubuntu, L.P.S public even with the LiveCD of ubuntu 12.04 and [B]the problem still there!!!!!!!!!!!!! 
What could it be? [/B]please help me!

---

### Post by varunendra on 2014-06-26
Does your network has a DHCP server? Usually the router between your ISP and the local network does this job, but you should make sure it has DHCP function and it is enabled. Refer to the router's user manual if you need help on this.

IF DHCP is enabled and working, please open a terminal in Ubuntu, and post back the outputs of these commands (to be entered one-by-one) :
```
sudo lshw -numeric -C network
nm-tool
route -n
cat /etc/network/interfaces
cat /var/lib/NetworkManager/NetworkManager.state
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by dylan0005 on 2014-06-26
Thanks @varunendra Now it only works when I turn off the modem completely and turn on again! That's not happened before! I'm confused...
Whatever here are the command outputs:
```

 *-network               
       descripción: Ethernet interface
       producto: L2 Fast Ethernet [1969:2048]
       fabricante: Atheros Communications Inc. [1969]
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth0
       versión: a0
       serie: 00:22:15:60:9f:b2
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=186.32.34.89 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:44 memoria:fbfc0000-fbffffff memoria:fbfa0000-fbfbffff

**nm-tool**------------------------------------------------------------------------------------------------------------------------------------------------------------------

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            atl2
  State:             connected
  Default:           yes
  HW Address:        00:22:15:60:9F:B2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         186.32.34.89
    Prefix:          23 (255.255.254.0)
    Gateway:         186.32.34.1

    DNS:             8.8.8.8
    DNS:             186.32.0.99

**route -n**---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask       Indic Métric Ref    Uso Interfaz
0.0.0.0         186.32.34.1     0.0.0.0         UG    0         0          0        eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0         0       eth0
186.32.34.0     0.0.0.0         255.255.254.0   U     1      0          0        eth0

 **cat /etc/network/interfaces**-----------------------------------------------------------------------------------------------------------------------
auto lo
iface lo inet loopback

**cat /var/lib/NetworkManager/NetworkManager.state**-----------------------------------------------------------------------------------------------------------------------------

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true
```

Please, excuse me if I didn't know how to use the code tags or how it works.

---

### Post by varunendra on 2014-06-28
Sounds again like a DHCP issue. In Network Manager, is the "Method" for "IPv4" set to "auto" or "Manual"?

I suggest you set it to "Manual" and fill in the IP, Subnet (will be filled automatically), Gateway, DNS Servers fields manually. Save and close Network Manager settings and reboot to check if the connection is stable.

---

### Post by dylan0005 on 2014-06-28
Well, I'll give it a try! Thank you for your comments and suggestions. Hope that works!

---

