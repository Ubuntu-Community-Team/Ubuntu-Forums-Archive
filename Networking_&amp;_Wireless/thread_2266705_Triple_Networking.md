---
title: "Triple Networking"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by VIctor_Oyervides on 2015-02-24
Hi , i recently buy a two port Network card , why ? beacuse in my network i have a server running ubuntu , my current network setup is that i have two separated LAN , the first one is where all my private stuff is , like dvr , office computers  , etc and i connect the server to this network using the motherboard ethernet port , my second network is the public one , where all guest in the hotel are and i need the server that also ahve coenction here because here is the Hotspot server and UniFi Controller so my server is conected to this network using one of the network Card port , and the other port in the card i plug it on the modem to get a second Public IP addres from my ISP (i have 5 public IP addres) , i ping the internal LAN IP and works , but when i try to ping the public IP asigned to my server it jsut donot work , im new here so please tell me witch config files i need to post 

here is my ifconfig:
eth0      Link encap:Ethernet  direcciónHW 74:d4:35:fa:e9:07
          Direc. inet:192.168.1.200  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::76d4:35ff:fefa:e907/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:42289 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46188 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:12940056 (12.9 MB)  TX bytes:44041687 (44.0 MB)


eth1      Link encap:Ethernet  direcciónHW 00:0a:cd:28:6c:b4
          Direc. inet:192.168.2.200  Difus.:192.168.2.255  Másc:255.255.255.0
          Dirección inet6: fe80::20a:cdff:fe28:6cb4/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:20733 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:16277 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:6373944 (6.3 MB)  TX bytes:10461874 (10.4 MB)


eth2      Link encap:Ethernet  direcciónHW 00:0a:cd:28:6c:b5
          Direc. inet:68.206.140.132  Difus.:68.206.143.255  Másc:255.255.240.0
          Dirección inet6: fe80::20a:cdff:fe28:6cb5/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:142060 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:143 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:8760818 (8.7 MB)  TX bytes:20432 (20.4 KB)


lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:119081 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:119081 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:50478042 (50.4 MB)  TX bytes:50478042 (50.4 MB)
(Sorry but the config is in spanish)

---

### Post by TheFu on 2015-02-25
I wouldn't do what you are trying. I would keep these networks completely separate and if any connectivity is needed between them, use a VPN. I tiny mistake could leave your business computers open to hacking. That wouldn't be good.

A dedicated business-specific router that splits the networks would be good or a relatively cheap box running pfsense or routerOS.  I'd have the server protected. by explicit firewall rules against the guest network too.

I had to look up "UniFi Controller" - so it seems there is a Ubiquiti device involved here somewhere. They make good stuff!  I've used pfsense on a small x86, 4 port, box with multiple ubiquiti wifi-APs connected before.

Perhaps if you posted a clear diagram of the network, we can better understand the other security aspects?

Lastly, it would be helpful if you could use "code tags" for all command output. Makes things line up and easier to read.

Assuming everything is good as architected, the output from **route** is needed.

---

