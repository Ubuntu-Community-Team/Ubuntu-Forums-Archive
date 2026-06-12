---
title: "DCHP lease issues"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by sidd on 2005-05-23
Hello all
recently installed ubuntu. 
uname -a reports
linux testbox 2.6.10-5-386 #1  i686 GNU/Linux

dhcp wont get a lease address from the network. if i plug the same cable to my laptop on which i am running windows xp , i get a lease address straight away. i plug the same cable back in to the ubuntu box and i wont get a lease address.
if i do a 
sudo ifup eth1 
sit0: unknown hardware address type 776
Listening on LPF/eth1/ ( mac address)
sending on LPF/eth1/( mac address)
sending on socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
no DCHPOFFERS RECIEVED
no working leases in persistent database - sleeping


can anyone guide me as to what is happening and how i can fix this problem.

ps: am using ubuntu for the first time ever.

tx
sidd

---

### Post by mirtux on 2005-05-24
Hi,
  are you sure that eth1 is your network card? It can be also eth0 (normally)....

Regards,
MC

---

### Post by logan2004 on 2005-05-24
please show us the output of ifconfig, is this your own home network?

---

### Post by sidd on 2005-05-25
There are two network cards on this box. 
the first one eth0 is a inbuilt intel adapter. thought ubuntu cant really work with these inbuilt ones.
so i got a 3com card in and tired using that.

anyway the output of ifconfig is down below

root@testbox:/home/#ifconfig
eth1 Link encap: Ethernet HWadddr (mac address)
inet6 addr: fe80::200:e2ff:fe43:da73/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0b) TX bytes:2052 (2.0KiB)

lo   Link encap : Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
net6 addr: ::1/128 Scope:host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:664434 errors:0 dropped:0 overrruns:0 frame:0
TX Packets:664434 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:51380007 (48.9 MiB) TX Bytes:51380007 (48.9 MiB)

root@testbox:/home#

Note: eth0 is down at the moment. have no cable connected and i have it turned off.

tx
sidd

---

### Post by sidd on 2005-05-25
is this problem unsolvable or something?
please help :(
sidd

---

### Post by mirtux on 2005-05-26
Hi,
   is it your card recognized by the kernel? What is the output of **dmesg | grep eth1**. It could be that the driver of your network card are not included in the standard kernel.

Regards,
MC

---

