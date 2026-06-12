---
title: "Toshiba laptop Ubuntu help with Wired Connection"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by tricky007 on 2008-09-07
well i dont know how to set the internet connecting.. i see the wired connection i go to properties i have tried everything but nothing seem to work + i have a username and password where do i have to put that ... i tried the pppoeconf in the terminal i get this blue thingy than it goes till 100% than stops there... if you need any info to help me plz ask and i will do my best thanks anywayz

---

### Post by superprash2003 on 2008-09-07
what connection are you using??dial up or dsl?

---

### Post by tricky007 on 2008-09-07
dial up

---

### Post by tricky007 on 2008-09-08
wait am not sure it is a dial up connection :( i dont know really how can i know ?

---

### Post by tricky007 on 2008-09-08
btw i dont need a phone number or something to connect just username and password that is how i connect from my windows xp i go to the network thingy make a protocol installation give it the browse to pppoe than create a dial up connection but in ubuntu i dont know how to do it and stuff 
plz help

---

### Post by lisati on 2008-09-08
If it's dial-up you'll need a phone number as well as a user name and a password. With *ubuntu you might also need to install a modem driver before trying to connect - my Toshiba laptop needs one for dial-up that I haven't bothered installing because I connect through an ADSL modem connected by ethernet.

EDIT: My adsl connection doesn't prompt me for user name or password, these are stored in the modem.

---

### Post by tricky007 on 2008-09-09
ok am guessing mostl likly i have a dsl connection...
when u write in the terminal 
sudo pppoeconf 
am getting an error after it is doing the search and stuff in my two devices eth0 and another one 
the error is 
"cannot aquire address "

help plz

---

### Post by superprash2003 on 2008-09-09
in the terminal type ifconfig and post output here

---

### Post by tricky007 on 2008-09-10
tricky@tricky:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:33:35:40:32  
          inet6 addr: fe80::21e:33ff:fe35:4032/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:3009565401 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6663 (6.5 KB)  TX bytes:4953 (4.8 KB)
          Interrupt:17 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1E:33:35:40:32  
          inet addr:169.254.3.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12728 (12.4 KB)  TX bytes:12728 (12.4 KB)

---

### Post by superprash2003 on 2008-09-11
ok the problem seems to be that you arent getting an ip on your machine.Presuming you have an external DSL modem connected via LAN.. whose ip address is 192.168.1.1 ..do the following..
  go to system->admin->network and go to eth0 properties and disable roaming mode and select static ip addresss and enter ip address as 192.168.1.10 and gateway as 192.168.1.1 .. now try sudo pppoeconf .. also type ping 192.168.1.1 in your terminal and post output

---

### Post by tricky007 on 2008-09-12
well i did as you said and put the sub mask as 255.255. something i guess the default...

but it is still didnt work :( when i put sudo pppoeconf the bar thingy is going till 100% than stopping there and nothing is happening... i tried pining the ip but i got this 

tricky@tricky:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable

---

### Post by tricky007 on 2008-09-18
anybody help plz

---

