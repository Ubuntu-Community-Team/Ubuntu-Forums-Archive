---
title: "HIgh pings over ethernet wired network"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by evozniak on 2008-07-27
hi my ping to router or others computers in LAN are 150+ in windows the pings are 1-2ms and copy files is so crappy, what is happening?

---

### Post by tamoneya on 2008-07-27
can you post the result of ```
ifconfig
sudo lswh -C network
```just so that we can familiarize ourselves with your setup.

---

### Post by evozniak on 2008-07-27
eduardo@eduardo:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:16:36:90:dc:51
          inet end.: 10.1.1.2  Bcast:10.255.255.255  Masc:255.0.0.0
          endereço inet6: fe80::216:36ff:fe90:dc51/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1137 erros:1 descartados:0 excesso:0 quadro:0
          Pacotes TX:999 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:1049246 (1.0 MB) TX bytes:197643 (193.0 KB)
          IRQ:11 Endereço de E/S:0xa000

lo        Link encap:Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:1726 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1726 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:86300 (84.2 KB) TX bytes:86300 (84.2 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:16:cf:b2:c7:43
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0  Link encap:Não Especificado  Endereço de HW 00-16-CF-B2-C7-43-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by evozniak on 2008-07-28
sorry
T-up

i need fix it.

---

