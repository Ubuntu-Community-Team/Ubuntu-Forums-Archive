---
title: "Desconfigurada red al reiniciar maquina"
date: 2021-02-20
forum: Networking &amp; Wireless
---

### Post by osjacpe on 2021-02-20
Saludos amigos, un buen día para todos.

Deseo consultar sobre el siguiente problema:

Tengo un servidor con 4 tarjetas de red, ubuntu server 20.04, tres de ellas en uso, cada una con ip statica, y  conectadas a un proveedor de internet diferente. Cada vez que reinicio la maquina la configuración de red al parecer cambia, pues debo cambiar físicamente los cables de red entre tarjetas hasta dar con la ubicación correcta de cada cable para que las tres conexiones de red funciones.

Acudo a ustedes solicitado ayuda para dar solución a este problema y poder reiniciar la maquina sin que la configuración de red cambie. Adjunto configuración actual de red.

auto lo ens1 eth0 eth2


iface lo inet loopback


# The primary network interface
allow-hotplug ens1 eth0 eth2

# Red fibra optica
iface ens1 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 190.157.8.33 181.48.0.233


# Red proveedor 1
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        broadcast 192.168.0.255


# Red proveedor 2
iface eth1 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        broadcast 192.168.2.255

---

