---
title: "Problem getting DSL modem to work"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by jollemeyer on 2007-04-21
On Ubuntu 7.04, I tried to get my DSL modem to work. My computer is fitted with an (inactive) ethernet connector (no cable attached) and an internal DSL modem. The manufacturers/models are as follows:

[INDENT]joerg@Phoenix:/etc/ppp/peers$ lspci
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:09.0 Network controller: AVM Audiovisuelles MKTG & Computer System GmbH Fritz!Card DSL SL (rev 01)[/INDENT]

In order to get the DSL modem to work, I installed the following packages as recommended in another thread:
[LIST]
[*]libcapi
[*]capiutils
[*]avm-fritz-firmware-2
[*]drdsl
[*]pppdcapiplugin
[/LIST]

Now, the DSL modem is detected correctly. The following confirms that the kernel modules for my DSL modem are loaded:
[INDENT]joerg@Phoenix:/etc/ppp/peers$ lsmod | grep fcdsl
fcdslsl               839200  0
kernelcapi             41172  2 fcdslsl,capi[/INDENT]

Also, when looking at dmesg, everything is fine:
[INDENT]joerg@Phoenix:/etc/ppp/peers$ dmesg | grep fcdsl
[  909.181975] fcdslsl: AVM FRITZ!Card DSL SL driver, revision 0.3.2
[  909.181983] fcdslsl: (fcdslsl built on Apr 13 2007 at 18:32:05)
[  909.181986] fcdslsl: -- 32 bit CAPI driver --
[  909.182984] fcdslsl: Loading...
[  909.183502] kcapi: Controller [001]: fcdslsl-4000-19 attached
[  909.183510] fcdslsl: Loaded.
[  909.186019] fcdslsl: Using VCC/VPI/VCI = 0x1/0x1/0x20
[  909.186361] fcdslsl: Stack version 3.11-07
[  911.692737] kcapi: card [001] "fcdslsl-4000-19" ready.[/INDENT]
I can also can test the internal settings of this modem, so everything seems to be fine with the card itself.

However, when I tried to establish a ppp0 interface to my ISP using "pon", I get some weird results:
[INDENT]joerg@Phoenix:/etc/ppp/peers$ pon ngi
Plugin capiplugin.so loaded.
capiplugin: $Revision: 1.36 $
capiconn:  1.13[/INDENT]

The ISP settings in "ngi" should be fine. I check them several times. It contains the following lines:
[INDENT]user myusername
noauth
plugin capiplugin.so
avmadsl
:
/dev/null[/INDENT]

The plog gives the following:

[INDENT]joerg@Phoenix:/etc/ppp/peers$ plog
Apr 20 18:15:57 Phoenix pppd[5667]: capiplugin: disconnect(remote): "" -> "" outgoing (pcli=0x101/ncci=0x10101) 0x0000 (0x3312) - No additional information
Apr 20 18:15:57 Phoenix pppd[5667]: capiplugin: couldn't make connection
Apr 20 18:15:57 Phoenix pppd[5667]: controller 1: listen_change_state 0 -> 1
Apr 20 18:15:57 Phoenix pppd[5667]: controller 1: listen_change_state state=1 event=1 ????
Apr 20 18:15:57 Phoenix last message repeated 2 times
Apr 20 18:15:57 Phoenix pppd[5667]: contr 1: listenconf Info=0x0000 (No additional information) infomask=0x144 cipmask=0x0 capimask2=0x0
Apr 20 18:15:57 Phoenix pppd[5667]: controller 1: listen_change_state 1 -> 0
Apr 20 18:15:57 Phoenix pppd[5667]: capiplugin: exit
Apr 20 18:15:57 Phoenix pppd[5667]: Exit.
Apr 20 18:15:57 Phoenix kernel: [ 1020.977654] kcapi: appl 1 ncci 0x10101 down[/INDENT]

The problem seems to be, that the ppp0 cannot be established using pppoe. I suspect this is because of my empty eth0, which the H/W address identifies as the unconnected Ethernet connector. ifconfig gives the following:

[INDENT]joerg@Phoenix:/etc/ppp/peers$ ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:30:05:5B:23:A7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ€nge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Basisadresse:0x3000 Speicher:ea000000-ea020000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 GÃŒltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ€nge:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/INDENT]

I tried to disable eth0, but it seems it gets activated whenever i try to establish a pppoe connection using "pon".

I also tried to setup my DSL modem using pppoeconf. 
This detects eth0 (unsued ethernet connector) and than tries to connect my Access Concentrator. Later on, it complains that it could not configure my pppoe. I don't have the message by hand, but it was something like "another interface was already active"
Ifconfig again ws unchanged, no ppp0 available.

What am I doing wrong? Ubuntu with no internet connection is no fun:( 

Any help is welcome.

---

