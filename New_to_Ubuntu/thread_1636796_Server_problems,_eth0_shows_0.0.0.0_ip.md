---
title: "Server problems, eth0 shows 0.0.0.0 ip"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by jgratero on 2010-12-03
I have a very particular issue with xubuntu...

I work in a non profit organization, and several of our oldest pc's are running xubuntu, the rest are on Vista, and XP. From time to time, we have problems with the DHCP server, and some pc's lose its IP (showing the default 169...). Most of the pc "off the grid" are the ones with xubuntu.

This is the output of ifconfig and dhclient on one of them

```
cpfa11@cpfa11-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:18:8b:20:f4:39  
          Dirección inet6: fe80::218:8bff:fe20:f439/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:11 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:10 
          Bytes RX:948 (948.0 B)  TX bytes:2520 (2.5 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:40 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:40 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:2904 (2.9 KB)  TX bytes:2904 (2.9 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:90:4b:63:36:e1  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

cpfa11@cpfa11-desktop:~$ sudo dhclient eth0
[sudo] password for cpfa11: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:18:8b:20:f4:39
Sending on   LPF/eth0/00:18:8b:20:f4:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```And this is what one of the Vista pc's do show, on ipconfig:

```
C:\>ipconfig /all

Configuración IP de Windows

   Nombre de host. . . . . . . . . : julia1
   Sufijo DNS principal  . . . . . :
   Tipo de nodo. . . . . . . . . . : híbrido
   Enrutamiento IP habilitado. . . : no
   Proxy WINS habilitado . . . . . : no
   Lista de búsqueda de sufijos DNS: cantv.net

Adaptador de Ethernet Conexión de área local:

   Sufijo DNS específico para la conexión. . : cantv.net
   Descripción . . . . . . . . . . . . . . . : Realtek RTL8168C/8111C Family PCI
-E Gigabit Ethernet NIC (NDIS 6.0)
   Dirección física. . . . . . . . . . . . . : 00-24-81-87-19-D4
   DHCP habilitado . . . . . . . . . . . . . : sí
   Configuración automática habilitada . . . : sí
   Vínculo: dirección IPv6 local. . . : fe80::e5f4:37c7:66f3:cd66%10(Preferido)

   Dirección IPv4. . . . . . . . . . . . . . : 200.109.189.129(Preferido)
   Máscara de subred . . . . . . . . . . . . : 255.255.224.0
   Concesión obtenida. . . . . . . . . . . . : jueves, 02 de diciembre de 2010 1
0:19:25
   La concesión expira . . . . . . . . . . . : jueves, 02 de diciembre de 2010 1
1:19:25
   Puerta de enlace predeterminada . . . . . : 200.109.160.1
   Servidor DHCP . . . . . . . . . . . . . . : 200.109.126.42
   IAID DHCPv6 . . . . . . . . . . . . . . . : 167781505
   DUID de cliente DHCPv6. . . . . . . . . . : 00-01-00-01-10-37-18-A1-00-21-5A-
21-9C-6A
   Servidores DNS. . . . . . . . . . . . . . : 200.44.32.12
                                       200.11.248.12
   NetBIOS sobre TCP/IP. . . . . . . . . . . : habilitado

Adaptador de túnel Conexión de área local*:

   Sufijo DNS específico para la conexión. . :
   Descripción . . . . . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface

   Dirección física. . . . . . . . . . . . . : 02-00-54-55-4E-01
   DHCP habilitado . . . . . . . . . . . . . : no
   Configuración automática habilitada . . . : sí
   Dirección IPv6 . . . . . . . . . . : 2001:0:4137:9e76:204e:5b4:3792:427e(Pref
erido)
   Vínculo: dirección IPv6 local. . . : fe80::204e:5b4:3792:427e%11(Preferido)
   Puerta de enlace predeterminada . . . . . :
   NetBIOS sobre TCP/IP. . . . . . . . . . . : deshabilitado

Adaptador de túnel Conexión de área local* 6:

   Estado de los medios. . . . . . . . . . . : medios desconectados
   Sufijo DNS específico para la conexión. . : cantv.net
   Descripción . . . . . . . . . . . . . . . : Adaptador ISATAP de Microsoft
   Dirección física. . . . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP habilitado . . . . . . . . . . . . . : no
   Configuración automática habilitada . . . : sí

Adaptador de túnel Conexión de área local* 7:

   Sufijo DNS específico para la conexión. . : cantv.net
   Descripción . . . . . . . . . . . . . . . : 6TO4 Adapter
   Dirección física. . . . . . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP habilitado . . . . . . . . . . . . . : no
   Configuración automática habilitada . . . : sí
   Dirección IPv6 . . . . . . . . . . : 2002:c86d:bd81::c86d:bd81(Preferido)
   Puerta de enlace predeterminada . . . . . : 2002:c058:6301::c058:6301
   Servidores DNS. . . . . . . . . . . . . . : 200.44.32.12
                                       200.11.248.12
   NetBIOS sobre TCP/IP. . . . . . . . . . . : deshabilitado

```One detail: The pc's that do have access to internet, have IP addresses way beyond the scope set on the two DHCP servers we have...

I'm definitively puzzled...

---

