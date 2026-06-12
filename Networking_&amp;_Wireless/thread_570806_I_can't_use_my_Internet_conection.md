---
title: "I can't use my Internet conection"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by marmundo on 2007-10-08
I installed my wireless card RT73. I can view the nets and I can connect and take a IP.
In Windows I can access internet with the next settings:
```
DNS server  . : fortalnet.com.br
IP . . . . . . . . . . . . : 10.241.153.2
net mask . . . . . . . . : 255.255.255.252
Gateway. . . . . . . . . . . : 10.0.0.1
```

The next commands will be in Ubuntu:

So, when I try ping some url, I have :
```
marcelo@manguaba:~$ ping www.uol.com.br
ping: unknown host www.uol.com.br
marcelo@manguaba:~$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 169.254.11.27 icmp_seq=1 Destination Host Unreachable
From 169.254.11.27 icmp_seq=2 Destination Host Unreachable
From 169.254.11.27 icmp_seq=3 Destination Host Unreachable

--- 10.0.0.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5012ms
, pipe 3

```

I red a lot of posts here and nothing works.
I will post my settings.

```
marcelo@manguaba:~$ ifconfig
ath0       Encapsulamento do Link: Ethernet  Endereço de HW 00:19:7E:02:58:88  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:D4:CA:CD:C2  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:18 Endereço de E/S:0x2000 

eth0:avah  Encapsulamento do Link: Ethernet  Endereço de HW 00:16:D4:CA:CD:C2  
          inet end.: 169.254.11.27  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:18 Endereço de E/S:0x2000 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:46 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:46 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:4324 (4.2 KiB) TX bytes:4324 (4.2 KiB)

wifi0      Encapsulamento do Link: Não Especificado  Endereço de HW 00-19-7E-02-58-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:43 erros:0 descartados:0 excesso:0 quadro:352589
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:199 
          RX bytes:2752 (2.6 KiB) TX bytes:0 (0.0 b)
          IRQ:20 

wlan0      Encapsulamento do Link: Ethernet  Endereço de HW 00:0E:2E:DA:D6:F5  
          inet end.: 10.241.153.2  Bcast:10.255.255.255  Masc:255.255.255.252
          endereço inet6: fe80::20e:2eff:feda:d6f5/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:2720 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:49 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:604229 (590.0 KiB) TX bytes:40486 (39.5 KiB)
  
```

```
marcelo@manguaba:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

iface ppp0 inet ppp
provider ppp0



auto wlan0
iface wlan0 inet static
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid qwe123
pre-up iwconfig wlan0 key off
address 10.241.153.2
netmask 255.255.255.252
gateway 10.0.0.1
wireless-essid qwe123


```
```

marcelo@manguaba:~$ netstat -r
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções   MSS Janela  irtt Iface
10.241.153.0    *               255.255.255.252 U         0 0          0 wlan0
link-local      *            255.255.0.0     U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 eth0

 
```
```

marcelo@manguaba:~$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 169.254.11.27 icmp_seq=1 Destination Host Unreachable
From 169.254.11.27 icmp_seq=2 Destination Host Unreachable
From 169.254.11.27 icmp_seq=3 Destination Host Unreachable

--- 10.0.0.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5012ms
, pipe 3


```
```

marcelo@manguaba:~$ ping www.uol.com.br
ping: unknown host www.uol.com.br

```

```

marcelo@manguaba:~$ sudo route add default gw 10.0.0.1 wlan0
SIOCADDRT: Network is unreachable

```

Resuming, I can get a valid IP but I can't ping a IP out my net.

Ps. I get a tracert on Windows to help!
```

C:\Documents and Settings\usuario>tracert www.uol.com.br

Rastreando a rota para www.uol.com.br [200.221.2.45]
com no máximo 30 saltos:

  1    27 ms    48 ms     *     10.0.0.1
  2    24 ms    20 ms    14 ms  192.168.38.1
  3    16 ms    18 ms    38 ms  200.209.216.1
  4   252 ms   264 ms   246 ms  embratel-S2-1-1-acc04.fla.embratel.net.br [201.3
0.250.1]
  5  2174 ms   342 ms   322 ms  ebt-G6-0-dist05.fla.embratel.net.br [200.244.169
.10]
  6   394 ms   291 ms   334 ms  ebt-P8-0-2-core03.rjo.embratel.net.br [200.244.1
60.54]
  7   354 ms   378 ms   291 ms  ebt-P12-1-core01.spo.embratel.net.br [200.230.1.
122]
  8   360 ms   339 ms   371 ms  ebt-C1-gacc03.spo.embratel.net.br [200.230.242.1
3]
  9   358 ms   322 ms   303 ms  peer-P2-2-gacc03.spo.embratel.net.br [200.211.21
9.126]
 10     *        *        *     Esgotado o tempo limite do pedido.
 11   491 ms   419 ms   512 ms  fr2-border5.ix.uol.com.br [200.221.30.41]
 12   514 ms   609 ms   347 ms  home.uol.com.br [200.221.2.45]

Rastreamento concluído.
```

---

### Post by helgman on 2007-10-08
> **marmundo said:**
> 
In Windows i can acess internet with the next settings:
```
DNS server  . : fortalnet.com.br
IP . . . . . . . . . . . . : 10.241.153.2
net mask . . . . . . . . : 255.255.255.252
Gateway. . . . . . . . . . . : 10.0.0.1
```

[...]

```
auto wlan0
iface wlan0 inet static
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid qwe123
pre-up iwconfig wlan0 key off
address 10.241.153.2
netmask 255.255.255.252
gateway 10.0.0.1
wireless-essid qwe123
```

You shouldn't be able to connect since your gateway is not on the same network as your wireless card. You wireless card is on the network 10.241.153.0 and you gateway is on the network 10.0.0.0. I don't understand why this works in Windows since Windows usually gives you a warning when you try this (I can't ignore the warning at the moment since that might make my Windows machine unreachable).

Are you connecting to a public network or a home router/AP?

Regards,
Helgman

---

### Post by marmundo on 2007-10-09
I'm connecting to a public network from a ISP. I think the problem is in my IP and in gateway. They are in differents sub-nets. How I sad, I can use in Windows. With tracert give the route from my computer to another host.

---

### Post by helgman on 2007-10-09
What routes do you have in Windows?
```
C:\ROUTE PRINT
```

Regards,
Helgman

---

### Post by marmundo on 2007-10-10
```
 
C:\Documents and Settings\usuario>ROUTE PRINT
===========================================================================
Lista de interfaces
0x1 ........................... MS TCP Loopback interface
0x2 ...00 0e 2e da d6 f5 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - M
iniporta do agendador de pacotes
0x3 ...00 19 7e 02 58 88 ...... Atheros AR5005G Wireless Network Adapter - Minip
orta do agendador de pacotes
0x10005 ...00 0e 2e da d6 f5 ...... RT73 USB Wireless LAN Card - Miniporta do ag
endador de pacotes
===========================================================================
===========================================================================
Rotas ativas:
Endereço de rede          Máscara   Ender. gateway       Interface   Custo
          0.0.0.0          0.0.0.0         10.0.0.1    10.241.153.2       30
     10.241.153.0  255.255.255.252     10.241.153.2    10.241.153.2       30
     10.241.153.2  255.255.255.255        127.0.0.1       127.0.0.1       30
   10.255.255.255  255.255.255.255     10.241.153.2    10.241.153.2       30
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0     10.241.153.2    10.241.153.2       30
  255.255.255.255  255.255.255.255     10.241.153.2               3       1
  255.255.255.255  255.255.255.255     10.241.153.2               2       1
  255.255.255.255  255.255.255.255     10.241.153.2    10.241.153.2       1
Gateway padrão:           10.0.0.1
===========================================================================
Rotas persistentes:
  Nenhuma


```

Thanks

---

### Post by helgman on 2007-10-11
If we compare the routes in Windows with the routes in Linux we see that Windows has a lot more of them. We also see that Linxus uses eth0 as default and that can't be good.

I assume that Windows picks up it's routes without any interaction? 

These two are interesting and totally missing in Linux:

```
Endereço de rede          Máscara   Ender. gateway       Interface   Custo
     10.241.153.0  255.255.255.252     10.241.153.2    10.241.153.2       30
   10.255.255.255  255.255.255.255     10.241.153.2    10.241.153.2       30
```

The same thing for the gateway:
```
Gateway padrão:           10.0.0.1
```

You could try adding them in Linux to get a similar setup:

```
route add -net 10.241.153.0 netmask 255.255.255.252 gw 10.241.153.2
route add -net 10.255.255.255 netmask 255.255.255.255 gw 10.241.153.2
route add default gw 10.0.0.1
```

But I can't get the last line, the one that sets the gateway, to work simply cause the gateway is on a network that we can't reach. You ISP don't have any information about this?

The "logical" way to set it us is to use 10.241.153.1 as a gateway since that is the only other host on the 10.241.153.0/30 network but that is NOT the setup is Windows.

Can you ping 10.241.153.1?

Regards,
Helgman

---

### Post by helgman on 2007-10-11
Well, I managed to "fool" my virtual machine having the same setup as you (wired).

I'm using VMware Server with a NAT interface given the IP address 10.0.0.2 and the NAT network has a gateway at 10.0.0.1.

The VM Ubuntu has the following network setup:
```
address 10.243.153.2
netmask 255.255.255.252
gateway 10.0.0.1
```
The gateway line in the configuration don't help much, it only produces an error (since we can't reach the network).

To add the routes I used the following:

```
route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.243.153.2
route add default gw 10.0.0.1
```

What I did above was tell the computer that it can reach any host from 10.0.0.0 to 10.255.255.255 on the interface with IP address 10.243.153.2 and then I told it that you can reach any host (that it don't have a route to) via 10.0.0.1.

I'm not sure it will work for you and I'm not sure what your ISP says about it but it worked for me.

Regards,
Helgman

---

### Post by marmundo on 2007-10-11
Thank's so much! With the last commands my net is on! Just a correction: route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.24**1**.153.2 Cause my IP is 10.241.153.2.

That's so funny. My ISP sad: "We don't support Linux". One day we will see people with a OPEN MIND! using OPEN SOFTWARE.

Again Thank you so much!

---

