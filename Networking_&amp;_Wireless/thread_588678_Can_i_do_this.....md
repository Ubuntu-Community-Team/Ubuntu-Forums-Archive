---
title: "Can i do this...."
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by blop on 2007-10-23
Hi all,

i have at home a DSL modem / router attached to a cisco switch that provides internet for my house. One cable is running upstairs to my main home machine, running XP Pro Sp2. Now it has two LAN cards and i wonder if i could use the unused LAN card to pump internet to my Ubuntu running laptop...

I do not want to run a second cable upstairs and i dont want to run wireless....

I have tried to the internet connection sharing wizard but not got anywhere with it...

I really really dont want to buy anything...no more flashing boxes to provide internet its getting crazu here!

---

### Post by sullenx on 2007-10-23
What you would need to do is bridge the two network cards and then allow NAT-ing.

---

### Post by blop on 2007-10-23
any idea of how i do that?

i thought i could use ICS but that does not seem to work..

---

### Post by kerry_s on 2007-10-23
nada

---

### Post by sullenx on 2007-10-23
Did you use a cross over cable when trying to do internet sharing? You might wanna look into that.

---

### Post by blop on 2007-10-23
I suspect there is some issue with ICS on a network that already has a router providing DHCP / DNS functionality...

There must be some way of doing it...

---

### Post by froy02 on 2007-10-23
The best way to connect 2 or more computer with your setup is buy another  network "switch" about $20 to $30.  Hook up the cable that is now hook up to your  computer to the uplink port of the new switch and then connect your computers to the other remaining  ports. You could get a 4  ports and be able to connect that many computers.
Note:  when you connect to uplink port, one of the ports is disabled so do not connect anything to that port.  The documentation would tell you which one.  To be on the safe side connect your computers to the middle ports of the switch.

A router would work just like a switch except you do not hook up anything lan port but it usually have an uplink port also. Brands: Dlink, Linksys, Netgear, etc.  I never had cisco so I could not say have they have.

---

### Post by blop on 2007-10-24
I really really do not want another box of any kind....

I really think there must be a method to allow my main xp machine to provide internet to my laptop through its spare NIC. There is a problem with Internet Connection Sharng and DHCP on a network so i need another solution....

---

### Post by bigken on 2007-10-24
highlight the two network connections in windows and bridge them use a crossover cable and manually assign the ip addresses   

ie win box 192.168.0.1
ubuntu box 192.168.0.2
subnet both machines 255.255.255.0
default gateway 192.168.0.1

its worth a shot

---

### Post by blop on 2007-10-24
HI Ken..

If i set those private addresses then i will be off the network that provides the machine internet...

I need to be on a 192.168.254.XXX network...

So will this work:

highlight the two network connections in windows and bridge them use a crossover cable and manually assign the ip addresses

ie win box 192.168.254.1
ubuntu box 192.168.254.2
subnet both machines 255.255.255.0
default gateway 192.168.254.254 (address of my modem / router / switch)

many thanks

---

### Post by bigken on 2007-10-24
just try it you cant hurt anything the ip addresses i gave you were just examples 
im not sure this will work but like i said its worth a try 

this how i have made two windows boxes work with each other I also installed  IPX or NetBEUI protocols

---

### Post by blop on 2007-10-24
I tried the bridge and set the IPs correctly but sadly that does not work...

what a pain....i cant believe its a hard thing to do.

The bridge recognises a connection at the end of the cable but no traffic is moved..

---

### Post by bigken on 2007-10-24
have you enabled internet connection sharing ?

---

### Post by blop on 2007-10-24
hey Ken,

you cant enable ICS on a bridged connection its one or the other...

there must be a guide on bridging somewhere...ill have a hunt.

---

### Post by bigken on 2007-10-24
good luck bet you find your answer with google

---

