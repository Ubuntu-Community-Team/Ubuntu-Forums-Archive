---
title: "ssh tunnel with vpnc with gateway"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by kwN7kft on 2015-04-24
Hi there,

I have the following cenario,

Source Server 
[LIST]
[*]    Ubuntu Server 12.10
[*]    VPNC -> to connect vpn to second server (cisco equipment but not managable by me)
[*]   ssh connection using vpnc.
[*]ip 10.50.120.32
[/LIST]

Destination Server

[LIST]
[*] Ubuntu Server 12.10
[*] Can connect ssh server but cannot return
[*] No connection to source machine
[*]ip 192.10.50.32
[/LIST]

Tried to establish ssh tunnel but without success .

Tried these:

SSH from the destination to the source (with public ip) using command below:

ssh -R 19999:localhost:22 root@10.50.120.32

   	
Obtained the following 

  ssh: connect to host 10.50.120.32 port 22: Connection timed out

I think that from destination to source I don't have gateway taht has been cuted by vpnc connection (or in cisco concentrator) .

What indeed I want to know if there is any possibility from source to destination open traffic through ssh tunnel that becomes bidirectional (comunication below vpnc in both ways (source<->destination)

Anyone to help ?

Thanks

---

### Post by kwN7kft on 2015-04-25
Hi there,

Do I must have tunneldigger or tun2socks ?
It will help for my problem ?

Anyone

---

