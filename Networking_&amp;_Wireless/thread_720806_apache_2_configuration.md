---
title: "apache 2 configuration"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by chemicalgr on 2008-03-10
Hello people
I'm using an apache2 server and a "friend" is trying to view my page from his pc 
when he types my ip adress it doesn't seem my apache to respond ,basically he can see my web page
in file ports.conf i'd already set my ip and the port , but nothing seems to go better than this.
Please help me ,thanks for your interest

---

### Post by SpaceTeddy on 2008-03-10
the information you have provided is a little... low :) maybe you want to share some more details so we can debug the problem better.

first off, what is your network setup ? how exactly is the computer that is running the webserver connected to the internet ? is there a router inbetween ? does it have port forwarding setup if there is one ?

as for the apache configuration. what directory have you put your page in ? what page exactly can your friend see ? does he get a timeout when trying to connect to you ?
have you remove the standard redirect from the default configuration ? have you written any virtual hosts yourself and have you enabled them ?

please try to answer as fully as you can. if you do not understand a question, tell what you don't get and i will try to provide you with commands/howtos on how to figure it out and how to fix the problem... hopefully anyways :)

---

### Post by chemicalgr on 2008-03-10
oh sorry
First off all i have dynamic ip ,and i'm connected via eth wire(UDP?)
Yes my speedstream modem/router has portforwarding setup.
My friend actually after typing the adress on his browser it seems  that timing out .also he tried to ping my adress and he got non response packets.
I think the problem is that i do not know what port forwarding means exactly,but i think i can do some job here with your guidance
ty.
forgot to mention that 2 days before i'd upgrade my feisty to gutsy and i didn't keep the last configuration on my apache2 the only configured is in the file ports.conf which i mentioned to you on my first message

---

### Post by SpaceTeddy on 2008-03-10
ok, if the port forwarind had worked, you would have seen a standard apache welcome page. So let's work on the redirecting of the traffic first.

What you need to do is the follow.
1.) figure out the IP address of your own computer (internally). this can be done with the command 
> ifconfig 
this should give you a whole heap if information, but the part you are acctually looking for looks like this one
```
eth1      Protokoll:Ethernet  Hardware Adresse 00:14:57:12:CD:26  
          inet Adresse:**192.168.0.127**  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::1123:71f1:f104:cd26/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1956754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2859090 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:100 
          RX bytes:1568463990 (1.4 GB)  TX bytes:2551226233 (2.3 GB)
          Basisadresse:0x6000 Speicher:d2800000-d2820000 

```
the bold part is your address. NOTE: you will always find at least two addresses. ignore the 127.0.0.1. that one is of no importance for this setup.

2.) note down the IP address. The next thing you need to do is log into your router and go into port forwarding. You need to forward Port 80 on tcp protocoll to the IP of your computer. This is usually a fairly straight process, but since the configuration pages for the routers differ to much i cannot tell you exactly what to do  here. 

so, the imporant bit is that you forward to YOUR ip (the one you found in step 1)
you must forward TCP protocoll
you must forward port 80 (sometimes it is called www or http aswell)

also, if you want your friend to be able to ping your computer, you will need to forward the icmp protocoll. Otherwise, your router will block the ping requests and nothing will return.

Hopefully that helps :)

---

### Post by chemicalgr on 2008-03-10
SpaceTeddy i'm not sure about that can we comnunicate via skype ?
my nick name is chemicalgr

---

