---
title: "shared internet but windows not getting internet"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by thyscorpion on 2007-11-12
hi , i am a intermediate newbie in linux and ubuntu.  i shared the internet using this step by step help : [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html")

I have two NIC cards on my ubuntu machine one is connected to the internet and the other to my windows laptop (xp)...
now when i use DHCP to try to connect the windows box to the ubuntu box.. it says limited connection. 
but when i use Static IP 192.168.0.100
my Ubuntu ip is 192.168.0.1 (connected to the windows box)
 it connect instantly but i dont get any internet on it. it shows not even a single byte is sent from the linux box to windows..
what am i doing wrong on my windows to make it work. or have i left a step (not given in the link above)?

Please help..

Thanks. :-)

---

### Post by aneeshkj on 2007-11-12
try setting the client pc's TCP/IP config as follows

**IP Address:**192.168.0.2
**Subnet Mask:**255.255.255.0
**Gateway:**192.168.0.1

and hope u have replaced **ethX**  and **ip** properly in that article...
(all of those steps were intended to be done on the server pc..)

---

### Post by thyscorpion on 2007-11-13
hi. :-) thanks for replying.
 yeah i tried it before also using the ip 192.168.0.100 :-) it didn't work.. ( it connected immediately but n packet was recieved by the client from the ubuntu machine.
i tried ur 192.168.0.2 also. but as i guessed the same problem remains.

 yes i did replace ethx with the eth0 in my case and also gave the ip 192.168.0.1

 because its connecting to the ubuntu machine shows me that the ubuntu box is accepting the statip ip and all. but not sharing the internet.. 

please advise. :-)

---

### Post by aneeshkj on 2007-11-16
in the first part of the tutorial u have to use the ethernet port that connects to the lan.. i mean the ethx

and in the second part of the tutorial u should replace ethx with the one that is used to connect o the net..

You should identify these two...
(May be eth0 and eth1)

---

