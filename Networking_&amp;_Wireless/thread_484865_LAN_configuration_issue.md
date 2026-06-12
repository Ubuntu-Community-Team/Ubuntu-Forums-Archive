---
title: "LAN configuration issue"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by pranav on 2007-06-26
I have a direct connection to the internet thru a static IP.

In windows xp & PCLinuxOS this is what i do (& my internet works... is always on... the moment i start the OS)-

I choose my LAN card n then assign the following:
IP address (given by the isp), 
subnet mask(255.255.255.0),
default gateway(given by the isp)
& the 2 DNS IPs... also given by the ISP.


In Ubuntu...thru System &#8594; Administration &#8594; Network, iit doesnt work... i cant understand why... i am doing the exact same thing elswhr n it is working... i'm sure that i didnt make a typo anywher... coz i've rechecked several times, to confirm... if possible pls give me directions to do this using the command line...

pls help me

---

### Post by t4thfavor on 2007-06-26
I know the configuration is stored in /etc/network/interfaces If you research that you may find which entries you will have to add to it in order for your configuration to work.

---

### Post by davecambs on 2007-06-26
I would recommend rebooting your PC and also your router / modem. There is no science in this answer, I know it has worked for me in the past !!

---

### Post by pranav on 2007-06-26
> I know the configuration is stored in /etc/network/interfaces If you research that you may find which entries you will have to add to it in order for your configuration to work.

i did that... these were the contents of the file ...
> eth0 inet static
address 192.168.54.124
netmask 255.255.255.0
gateway 192.168.54.1

what wud be the syntax to put in the dns1 & dns2 entries?

---

### Post by t4thfavor on 2007-06-26
I have no idea what the syntax is, but that is the problem. I would imagine it would be something like  "nameserver 192.168.54.1".

---

### Post by kevdog on 2007-06-26
Something like this perhaps:

address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0

---

### Post by encho on 2007-06-27
Nameservers are kept in separate file: /etc/resolv.conf

Contents of the file would be something like:

> 
nameserver 192.168.54.1
nameserver 192.168.54.10


representing dns1 and dns2 respectively. You can put dns3 etc if you want.

You need to restart the network with: sudo /etc/init.d/networking restart

But usualy all this could be done through network settings (did you chech all the tabs?).

---

