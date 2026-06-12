---
title: "Wireless works in home but not in college"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Nighto on 2007-03-21
Hi,
i got a problem with my wireless card. It works OK in home, but surprisingly it doesn't in college. I've tried GUI and CLI solutions, but they didn't worked.
I use Ubuntu Feisty Fawn Herd 5 with 2.6.20.12-generic kernel, but i tried with an Edgy live cd and it didn't worked too.

here is my **ifconfig** at home:
```

eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12  
          inet end.: 192.168.0.104  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::216:cfff:fe92:a012/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:3970761 erros:0 descartados:85675 excesso:0 quadro:0
          Pacotes TX:2104117 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:1634199198 (1.5 GiB) TX bytes:131801295 (125.6 MiB)
          IRQ:255 Endereço de E/S:0x4000 

eth1       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:36:9B:0D:46  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:16 

eth1:avah  Encapsulamento do Link: Ethernet  Endereço de HW 00:16:36:9B:0D:46  
          inet end.: 169.254.3.230  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:16 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:28 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:28 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:2377 (2.3 KiB) TX bytes:2377 (2.3 KiB)


```
**eth0** is my wireless card. it catches that ip (192.168.0.100+) via dhcp.

also, my **iwlist eth0 scan** at home:
```

eth0      Scan completed :
          Cell 01 - Address: 00:16:B6:CB:FE:91
                    ESSID:"culturadigital"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-25 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 24ms ago

```

and it works flawlessly. but, when i come to college:
```

eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12  
          inet end.: 172.16.1.65  Bcast:172.16.1.255  Masc:255.255.255.0
          endereço inet6: fe80::216:cfff:fe92:a012/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:322 erros:0 descartados:408 excesso:0 quadro:0
          Pacotes TX:186 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:32127 (31.3 KiB) TX bytes:11427 (11.1 KiB)
          IRQ:255 Endereço de E/S:0x8000 

eth1       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:36:9B:0D:46  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:16 

eth1:avah  Encapsulamento do Link: Ethernet  Endereço de HW 00:16:36:9B:0D:46  
          inet end.: 169.254.3.230  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:16 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:15 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:15 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:1360 (1.3 KiB) TX bytes:1360 (1.3 KiB)

```
```

eth0      Scan completed :
          Cell 01 - Address: 00:4F:62:04:DB:45
                    ESSID:"corredor03"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-68 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 84ms ago

```
and i have to boot Windows to use my notebook :( 
In a friend of mine's notebook, which runs Ubuntu, works perfectly (just have to type iwconfig eth1 essid corredor0x (the name of network) and dhclient eth1), but in mine the dhclient eth0 just doesn't work.

My config is:
```

(Acer TravelMate 2480-2551)
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Any clues?

---

### Post by Austin_KW on 2007-03-21
grep eth0 /etc/network/interfaces

Is it set for your home network essid/encryption

---

### Post by Nighto on 2007-03-21
> **Austin_KW said:**
> grep eth0 /etc/network/interfaces

Is it set for your home network essid/encryption

```

nighto@acerola:~$ grep eth0 /etc/network/interfaces
auto eth0
iface eth0 inet dhcp

```

both are open, not-encripted networks.

---

### Post by Austin_KW on 2007-03-21
```
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12  
          inet end.: 172.16.1.65  Bcast:172.16.1.255  Masc:255.255.255.0
```
you are connected to your college network; you have a dhcp address,
It is probably a default route or dns problem
[INDENT]so check your default route with "route"
and your dns server with "cat /etc/resolv.conf" and try a dns lookup with "dig google.com"
[/INDENT] One of these might be set to your home network by the network manager?

---

### Post by DavidW2 on 2007-03-21
Looking at your output from ifconfig, you are getting an IP address at the college site.  It is 172.16.1.65.  The problem I am guessing is you can't browse the web.  If you can ping another host's IP then you need to check your Gateway or DNS settings.  Do you have either of those set in your /etc/network/interfaces file?

---

### Post by Nighto on 2007-03-23
> **DavidW2 said:**
> Looking at your output from ifconfig, you are getting an IP address at the college site.  It is 172.16.1.65.  The problem I am guessing is you can't browse the web.  If you can ping another host's IP then you need to check your Gateway or DNS settings.  Do you have either of those set in your /etc/network/interfaces file?

> **Austin_KW said:**
> ```
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12  
          inet end.: 172.16.1.65  Bcast:172.16.1.255  Masc:255.255.255.0
```
you are connected to your college network; you have a dhcp address,
It is probably a default route or dns problem
[INDENT]so check your default route with "route"
and your dns server with "cat /etc/resolv.conf" and try a dns lookup with "dig google.com"
[/INDENT] One of these might be set to your home network by the network manager?

ok, a got a cable, so right now i'm connected to the college network via cable, so i'm wired.
after "dhclient eth1" (my ethernet port is eth1), that's what i got:

```
root@acerola:/usr/local/FretsOnFire# ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:91 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:229 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:9254 (9.0 KiB) TX bytes:9558 (9.3 KiB)
          IRQ:255

eth1       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:36:9B:0D:46
          inet end.: 172.16.1.81  Bcast:172.16.1.255  Masc:255.255.255.0
          endereço inet6: fe80::216:36ff:fe9b:d46/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1357 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:581 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:696619 (680.2 KiB) TX bytes:135488 (132.3 KiB)
          IRQ:16

eth0:avah  Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12
          inet end.: 169.254.6.69  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:255

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:785 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:785 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:46330 (45.2 KiB) TX bytes:46330 (45.2 KiB)

```

what's up with that "avah"?

```

root@acerola:/usr/local/FretsOnFire# cat /etc/resolv.conf
search uniriotec.local
search metarec
nameserver 172.16.1.2

```

```

root@acerola:/usr/local/FretsOnFire# route
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
172.16.1.0      *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     0      0        0 eth0
default         172.16.1.1      0.0.0.0         UG    0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth0

```

```

root@acerola:/usr/local/FretsOnFire# dig google.com

; <<>> DiG 9.3.4 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44519
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             300     IN      A       64.233.187.99
google.com.             300     IN      A       72.14.207.99
google.com.             300     IN      A       64.233.167.99

;; AUTHORITY SECTION:
google.com.             145574  IN      NS      ns1.google.com.
google.com.             145574  IN      NS      ns2.google.com.
google.com.             145574  IN      NS      ns3.google.com.
google.com.             145574  IN      NS      ns4.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.         1180    IN      A       216.239.32.10
ns2.google.com.         1180    IN      A       216.239.34.10
ns3.google.com.         1180    IN      A       216.239.36.10
ns4.google.com.         1180    IN      A       216.239.38.10

;; Query time: 247 msec
;; SERVER: 172.16.1.2#53(172.16.1.2)
;; WHEN: Fri Mar 23 18:57:29 2007
;; MSG SIZE  rcvd: 212

```

but if i take out the cable, "ifconfig eth1 down", "dhclient eth0":

```

root@acerola:/usr/local/FretsOnFire# ifconfig eth1 down
root@acerola:/usr/local/FretsOnFire# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6206
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:cf:92:a0:12
Sending on   LPF/eth0/00:16:cf:92:a0:12
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

but, contrary to what it says, it gots an ip:

```

root@acerola:/usr/local/FretsOnFire# ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:91 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:257 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:9254 (9.0 KiB) TX bytes:10734 (10.4 KiB)
          IRQ:255

eth0:avah  Encapsulamento do Link: Ethernet  Endereço de HW 00:16:CF:92:A0:12
          inet end.: 169.254.6.69  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:255

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:791 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:791 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:47178 (46.0 KiB) TX bytes:47178 (46.0 KiB)

```

```

root@acerola:/usr/local/FretsOnFire# route
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

i noticed that when i'm wired, it takes some time to appear all 4 lines, but wirelessly it just appear these two lines above, instantly. don't know what to do.

```
root@acerola:/usr/local/FretsOnFire# dig google.com

; <<>> DiG 9.3.4 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

help me pleeease :-/

---

### Post by Austin_KW on 2007-03-24
This is different to your first post, where you were getting an address from the newtork (172.16.1.65)

In this case something (avahd) is assigning a local private address 169.254.6.69. This is really only used for an adhoc type network. You do not appear to be on the college network. You have missed a step somewhere.

Does 'iwconfig eth0' tell you if you have associated with your college network? I am guessing not. 
How are you telling eth0 which network to associate (connect) on. You need to add the college essid to /etc/network/interfaces or use some wifi network manager.

---

### Post by Austin_KW on 2007-03-24
try
sudo ifdown eth0
sudo iwconfig eth0 essid "corredor03"
sudo ifup eth0 (or sudo dhclient eth0)

and then look at your default route and dns server
 route
 cat /etc/resolv.conf

---

