---
title: "Sagem 800 - USB Modem"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by nog_man on 2008-05-21
Hi guys.

I have a Ubuntu 8.04 Hardy install and i'am struggling to get my Sagem 800 modem working...
After reading lots of info i'am almost ready to give up... but i decided to give it one last try at this forum:

I installed the deb package from [http://eagleedgy.c-webhosting.org.nyud.net:8080/installationSagem.html](http://eagleedgy.c-webhosting.org.nyud.net:8080/installationSagem.html)

ifconfig gives the folowing result:
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ec:6a:c8   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 Base address:0x1800  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2046 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2046 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:103428 (101.0 KB)  TX bytes:103428 (101.0 KB) 
 
nas0      Link encap:Ethernet  HWaddr 00:60:4c:ec:34:ea   
          inet6 addr: fe80::260:4cff:feec:34ea/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:46 (46.0 B)  TX bytes:5568 (5.4 KB)

For more info see attachments,

Any ideas on what's wrong?
Tanks in advance,

Nog

---

### Post by YokoUno on 2008-05-21
You have a type III fast800. If the package you are using does not help, then it might be an error of configuration of your own.

Does your ISP require that you use PPPoA or PPPoE? With what VPI/VCI? With what encapsulation?
Your ISP must be crystal clear about these params, and you must be aware of them to configure accordingly.

Anyway, the message "modem is operational" shows that you are close to getting this to work :)
You should get rid of Network Manager and avahi-autoipd which get in the way nastily with this kind of devices.

---

### Post by nog_man on 2008-05-26
Thanks for the help YokoUno.

I did as you said and uninstalled Network Manager and avahi-autoipd, but still no progress...

As for the ISP configuration, I played arround a bit with the params...

The ISP params are located in the fai-isp.txt file:
```
key;ISP-Fournisseur-d'accès;Pays;VPI;VCI;hexa;encapsulation;connexion; encryption;login/pwd;DNS-1;DNS-2;DNS-3;modem-fourni/testé
[...]
PT01;PT;Portugal;0;35;23;1;pppoe;;asxxxxxxxx@sapo; ;;;
PT02;Sapo-ADSL;Portugal;0;35;23;1;pppoe;;asxxxxxxxx@sapo;;19 4.79.69.22;194.70.69.222;
[...]
#2006-11-28-01:25:51-PropriÃ©taire-:-BenoitAudouard
#2007-10-20-09:56:12-Adaptation-:-Thierry-Valente
```

Has you can see, the file as two "accounts" the original is PT01. I added PT02, with DNS addresses that I grabbed from this site [http://www.guiaubuntupt.org/wiki/index.php?title=Lista_de_servidores_DNS_em_Portuga](http://www.guiaubuntupt.org/wiki/index.php?title=Lista_de_servidores_DNS_em_Portuga) l (Portuguese)

I tried both accounts with no sucess, also tried changing from pppoe to pppoa, by changing the “encapsulation” settings to 6 and “connexion” to pppoa, but still nothing…

Encapsulation 1 is RFC2516 Bridged PPoE LLC, and encapsulation 6 is RFC2364 PPoA VCmux.

Ifconfig now gives the following result:
```
nog@nog-laptop:~$ ifconfig
lo Link encap:Local Loopback 
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 addr: ::1/128 Scope:Host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:1870 errors:0 dropped:0 overruns:0 frame:0
   TX packets:1870 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0 
   RX bytes:102564 (100.1 KB) TX bytes:102564 (100.1 KB)
```

:confused:

---

