---
title: "strange behavior when setting static ip for eth1 in feisty"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by nyex on 2007-06-30
hello,

(sorry if my english is a bit rugged, it's not my native tongue).

since i've installed feisty i've been having a weird problem with the network configuration, which didn't happen when i was running edgy.

i have cable internet that uses eth0 and then my computer is connected to another computer (eth1), running windows, with which i share the internet access, etc.

trouble is, that unlike it used to be with edgy, i can't seem to make eth1 to have an static ip. actually, if i configure eth1 to an static ip, internet access through eth0 stops working, and i can't seem to connect anymore.

what i've been doing, and that have been working, is to leave eth1 as dhcp and every time the other computer is on and connect, i type in the console: "sudo ifconfig eth1 192.168.10.1 netmask 255.255.255.0 up"

this way, the other computer can surf the web with no problem at all. if i type "cat /etc/network/interfaces", though, i'll get:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


and, yet, if the other computer cable unplugs for some reason (it's a bit loose), i have to type that first command again ("sudo ifconfig eth1 192.168.10.1 netmask 255.255.255.0 up"). sometimes i don't, sometimes it keeps connects even if the cable unplugs. but if the windows computer is turned off and then on, there i go typing the command again.

with the windows computer connected and surfing the web, "ifconfig" shows:

eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:01:02:D1:8C:AB 
          inet end.: 192.168.1.3  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::201:2ff:fed1:8cab/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:176873 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:144997 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:120710985 (115.1 MiB) TX bytes:28886941 (27.5 MiB)
          IRQ:19 Endereço de E/S:0x8000

eth1       Encapsulamento do Link: Ethernet  Endereço de HW 00:08:54:E0:FA:19 
          inet end.: 192.168.10.1  Bcast:192.168.10.255  Masc:255.255.255.0
          endereço inet6: fe80::208:54ff:fee0:fa19/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:45631 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:67038 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:14466309 (13.7 MiB) TX bytes:45442349 (43.3 MiB)
          IRQ:20 Endereço de E/S:0x2000

lo         Encapsulamento do Link: Loopback Local 
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:2 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:2 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

ppp0       Encapsulamento do Link: Protocolo Ponto-a-Ponto 
          inet end.: 201.13.1.24  P-a-P:200.100.11.71  Masc:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Métrica:1
          pacotes RX:176105 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:144061 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:3
          RX bytes:116789467 (111.3 MiB) TX bytes:25638767 (24.4 MiB)


i've been using ubuntu for about six months now, and i'm not any kind of expert, so i have no idea of where to start looking for the solution.

does anyone have any idea of what may be happening, and how to solve it, so that i can make eth1 static and still get eth0 up and working with the internet?

---

### Post by spd106 on 2007-07-06
Set eth1 to be static by modifying the interfaces file. But don't add any gateway or dns addresses as these could conflict with the ones given to eth0.
i.e.
```
iface eth1 inet static
address 192.168.10.1
netmask 255.255.255.0
```

What are you using to set up port forwarding across this machine? Do you have ipmasq and dnsmasq?
This wiki page might be useful.
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

