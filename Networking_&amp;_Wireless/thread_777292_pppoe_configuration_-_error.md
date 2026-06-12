---
title: "pppoe configuration - error"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Puchacz1 on 2008-05-01
Hi. I want to set my connection to the internet but i've got a little problem :). When I run a terminal a try to start pppoeconf my system returned error

>   Sorry, I scanned 2 interfaces, but the Access                      
            Concentrator of your provider did not respond. Please              
            check your network and modem cables. Another reason               
            for the scan failure may also be another running pppoe            
            process which controls the modem.
I don't know why... I've 3 filles, may they will help you.

one of them :

> iface eth0 inet dhcp
addressXX.X.X.XX
netmaskXX.XX.XX.X
gatewayXX.XX.X.X
address XX.XX.XX.XX
netmask XX.XX.XX.X
gateway XX.XX.XX.XX



iface dsl-provider inet ppp
pre-up /sbin/ifconfig ath0 up # line maintained by pppoeconf
provider dsl-provider


iface ath0 inet static
address XX.XX.XX.XX
netmask XX.XX.XX.XX
gateway XX.XX.XX.XX
wireless-essid zawodzie



auto ath0



auto eth0
 
second 

> auto eth0
iface eth0 inet static
XX.XX.XX.XX
XX.XX.XX.XX
XX.XX.XX.XX


Could someone help me ?. I'm really desperate becouse I have tried repair it few days. Sorry for my language. I hope you understand me :).

---

### Post by Avail on 2008-09-19
Ive also got the same problem , mine works in windows but not linux

---

### Post by PocketDog on 2008-09-19
A pppoe connection has to have an MTU of 1492 (bytes) or less. If it's set at 1500 it may not work. This isn't a definitive solution but it's worth checking - (edit) sorry, this may have helped a broken pppoe connection, not a broken pppoeconf. My apologies

---

