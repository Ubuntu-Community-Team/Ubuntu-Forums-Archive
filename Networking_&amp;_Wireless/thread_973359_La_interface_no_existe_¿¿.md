---
title: "La interface no existe ?¿?¿?"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by dragonchanger on 2008-11-06
Hola a todos,
a ver quien me puede solucionar esto.

Tengo instalado Ubuntu Hardy 8.04 con la red funcionando perfectamente.
Enredando en el sistema quise ver la configuracion de la tarjeta de red (en Sistema->Centro de control->Herramientas de red, selecciono eth0, me muestra las estadisticas de interface sin problemas(navego perfectamente)  y al pinchar en "configurar"... me sale el mensaje :

La interface no existe
"Compruebe que el dispositivo esté escrito correctamente y que esté soportado por su sistema."

El servidor Xkai Link y el firestarter me dicen lo mismo y no los puedo usar.

Os posteo confs:

lshw -C Network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:10:dc:c6:b4:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.50 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s

:/etc/network# more interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

He leido muchos post del tema y nada, no hay manera HELPPP

Graciassss:KS

---

### Post by dragonchanger on 2008-11-10
Bueno, ya veo que tiene dificil solucion que nadie contest :)

---

### Post by andreshdz on 2009-03-20
> **dragonchanger said:**
> Hola a todos,
a ver quien me puede solucionar esto.

Tengo instalado Ubuntu Hardy 8.04 con la red funcionando perfectamente.
Enredando en el sistema quise ver la configuracion de la tarjeta de red (en Sistema->Centro de control->Herramientas de red, selecciono eth0, me muestra las estadisticas de interface sin problemas(navego perfectamente)  y al pinchar en "configurar"... me sale el mensaje :

La interface no existe
"Compruebe que el dispositivo esté escrito correctamente y que esté soportado por su sistema."

El servidor Xkai Link y el firestarter me dicen lo mismo y no los puedo usar.

Os posteo confs:

lshw -C Network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:10:dc:c6:b4:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.50 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s

:/etc/network# more interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

He leido muchos post del tema y nada, no hay manera HELPPP

Graciassss:KS

A mi me acaba de suceder algo muy parecido, pero esto fue por mi culpa, estaba jugando con algunas otras cosas y magicamente la maquina se congelo (tengo un don para lograr eso) asi que la reinicie a la fuerza y despues de eso tube el mismo problema, aparentemente estaba conectada (pero quien sabe donde) y cuando trataba de entrar a la configuración me marcaba el mismo error.

Supongo que al reiniciar a la fuerza de daño o quedo mal algún archivo de configuración y lo que yo hice fue reinstalar los linux-resticted-modules que ya estaban previamente instalados conectándome atraves del infalible cable :P Ahora funciona sin problemas. Puedes ver los módulos instalados y reinstalarlos desde el Synaptic.

Espero ser de ayuda.

---

