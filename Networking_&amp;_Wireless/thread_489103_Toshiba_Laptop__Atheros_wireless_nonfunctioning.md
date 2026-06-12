---
title: "Toshiba Laptop / Atheros wireless nonfunctioning"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by aqk on 2007-07-01
I have a new Toshiba laptop with an Atheros wireless card running Ubuntu 7.04 and MS-Vista under dual boot.
When running the Ubuntu, my wired Ethernet connects OK to the Access-point, but the Atheros doesn't seem to 'see' anything even though it appears OK . 
  I have loaded all the "latest'n'greatest" updates to Edgy Eft through the Synaptics pkg-manager.
Update Manager reports there is nothing to update anymore.

 Following is an ifconfig of both devices- 
 
 $ ifconfig
[B]ath0      Link encap:Ethernet  HWaddr 00:16:E3:F4:65:AC  
          inet addr:192.168.1.10  Bcast:192.168.1.31  Mask:255.255.255.224
          inet6 addr: fe80::216:e3ff:fef4:65ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/B]

[B]eth0      Link encap:Ethernet  HWaddr 00:A0:D1:74:11:A9  
          inet addr:192.168.1.11  Bcast:192.168.1.31  Mask:255.255.255.224
          inet6 addr: fe80::2a0:d1ff:fe74:11a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13548888 (12.9 MiB)  TX bytes:2808307 (2.6 MiB)
          Interrupt:20 Base address:0x800  [/B]

  I have tried disabling one or the other by either yanking out the Cat5 cord or turning off the wireless switch, but only the eth0 seems to recognize my network.
  Currently both are activated, but only the eth0 seems to allow me connectivity.
  I'm using static addrs for them, with  192.168.1.10 for eth0 and 192.168.1.11 for the wireless. 
In all other respects  (DHCP, DNS, etc) the two cards are configured similarly.

 If I switch over from Ubuntu to MS Vista using same network config, there is no problem with either connection.

  Any suggestions as to why the ath0 is so uncooperative?

    Thanx...

---

### Post by aqk on 2007-07-01
):P
   Ah surely would like to get this ath0 workin' so I can cut this here Cat5 umbilical cord free from the USRobotics mothership router.....

I'm using WEP now. I know I should be usng WPA2, but maybe I'll  remove the WEP and concentrate on getting the ath0 working with no encryption whatever. 
 Once** and if** it works, I'll switch to WPA2.  

  Any suggestions, anyone?  

  [SIZE="1"] (My pinoqachole level is getting VERY low....)[/SIZE]    ](*,)

---

### Post by ugm6hr on 2007-07-01
Look at the output of ```
lspci
```
You are interested in the Ethernet/Network Controller information (that should mention Atheros AR*xxxxX*).
Search here for the *specific* Atheros chipset (i.e. the AR*xxxxX* bit), and see if anyone has an answer.

Bear in mind that the madwifi driver doesn't behave itself with all atheros chipsets.

PS: clarify whether it is Ubuntu7.04 (i.e. Feisty) or 6.10 (Edgy) you are running.

---

