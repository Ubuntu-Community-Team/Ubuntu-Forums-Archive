---
title: "problema con ubuntu 8.04 y Huawei MT882 por eth"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by gpuccini on 2008-10-27
Hola,

hace varios días que estoy tratando de configurar el Huawei MT882 de arnet con ethernet, tengo instaldo el kubuntu 8.04. El pppoeconf me tira "no conectado..." y otras chorradas. He probado con la "configuración de red" pero tampoco funciona. No sé si la placa está bien configurada o que no se puede conectar con el modem/router: si hago [http://10.0.0.2/admin.html](http://10.0.0.2/admin.html) el navegador no puede abrir la página. Un dato importante es que la placa funciona perfectamente porque en la partición de Windown no tengo problemas... 

¿Qué puedo hacer?

Saludos,
Gabi

---

### Post by eder.apt-get on 2008-10-27
Necessitamos de mas informaciones. Qual es este IP 10.0.0.2? El modem? Es una coneccion DSL? No puedo ayudar te, pero yo voy traducir para el ingles la tu dubida.

---

### Post by eder.apt-get on 2008-10-27
I´m translating her doubt. maybe somebody else might help her out: there´ve been some days that I have been trying to configure Huawei MT882 arnet with ethernet, and I have kubuntu 8.04 installed. Pppeconf shows me "not conected"...and something more. I have tried the "red configuration" but it did´t work either. I don´t know if the problem is on a misconfig. of my board. It can´t connect to the modem/router: if I do [http://10.0.0.2/admin.html](http://10.0.0.2/admin.html), the browser can´t open the page. However, in my Window$ partition, the connecion works just fine...

---

### Post by gpuccini on 2008-10-27
> **eder.apt-get said:**
> Necessitamos de mas informaciones. Qual es este IP 10.0.0.2? El modem? Es una coneccion DSL? No puedo ayudar te, pero yo voy traducir para el ingles la tu dubida.

Muchas gracias por tu respuesta. Aquí va más información:
Hello, here you can find more information:


gabriel@gabi:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:06:4f:5e:71:e6
          dirección inet6: fe80::206:4fff:fe5e:71e6/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupción:16 Dirección base: 0xe800

lo        Link encap:Bucle local
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



gabriel@gabi:~$ sudo dhclient
[sudo] password for gabriel:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:06:4f:5e:71:e6
Sending on   LPF/eth0/00:06:4f:5e:71:e6
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.4 from 10.0.0.2
bound to 10.0.0.4 -- renewal in 40487 seconds.


gabriel@gabi:~$ lspci | grep Ethernet && lspci | grep modem
00:0c.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)


Por favor, decime si necesitas algo más.
Please, tell me if you need more information.
 
Gabi


%%%%%%%%%%%%%%%%

---

### Post by knix on 2008-10-27
I'm sory this is in English, but...

Here's my thoughts:
If you have a router, then you will be connecting via dhcp, not pppoe. If you are connecting directly to a DSL modem, you will have pppoe. I do not know about cable internet.

Anyway, it would be handy to know
1) What kind of internet connection you have.
2)whether you have a router, or connect directly to the modem.

Because of the IP addresses you mentioned, I assume you have a router. In this case, pppoeconfig is quite likely to not display a connection, as you are connected via dhcp. Actually, dhcp is more natively supported in linux. Try visiting or [www.google.com](www.google.com) in a browser, or pinging it in a terminal. You could also ping your router.
to ping, use
ping [www.google.com](www.google.com), or
ping 10.0.0.2
the linux ping does not set a limit on number of packets by default, so you will have to set that when ou ping, or just stop the ping with ctrl+c. I find stopping the ping is simpler.

Good Luck.

---

### Post by gpuccini on 2008-10-27
Thanks for your reply! I don't know if you have read my last post where I put additional information. Any way, Huawei MT882 is a modem/router, that is, it has both USB and Ethernet ADSL connections. I am trying to use my ethernet card.  

Of course, I could not ping [www.google.com](www.google.com), however I can ping my router (10.0.0.2). It is important to note that, as I said before, I can't open [http://10.0.0.2/admin.html](http://10.0.0.2/admin.html).

Please, tell me any other information you need.
Gabi

---

### Post by gpuccini on 2008-10-27
Pude solucionar el problema. Es importante que tengan en cuenta que hay varias cosas que, me parece, no funcinan muy bien: 
 
1) KNetworkManager: tube que hacer la configuracion manual (saque los datos de window$), pero en el icono de la derecha sigue indicando "desconectado".

2) Konqueror no me funciona. Tuve que instalar en mozilla y ahora puedo navegar. Recuerden que kubuntu 8.04 esta recien instalado. 

Me gustaria que alguien me aclarara porque pasan estas cosas. Si bien ahora puedo navegar al exterior, no quedo conforme.

Muchas gracias,

---

### Post by eder.apt-get on 2008-10-27
Yep! Sometimes we found out by ourserves what happened, but we don´t quite undesrtand :)
1)Maybe Knetwork thinks your pc is connected through USB, instead of eth0, or vice-versa;
2) That´s allright. Konqueror sucks anyway. I could be just the Konqueror setting.

---

### Post by knix on 2008-10-27
try installing firefox. I can't seem to recall ever getting konqueror to work for web browsing.
```
sudo apt-get install firefox
```
unless firefox is installed by default. I can't recall.
couple other thoughts:
you might install elinks (a command line web browser) and try accessing the admin page that way.
I don't know that running dhclient will do you any good on a pppoe connection.
Honestly I like the gnome network tools (particularly in intrepid) a litte better, but that's beside the point.
Also, you might see if there are any dhcp settings on the router/modem that might help.(i.e., boot into windows to check)

---

