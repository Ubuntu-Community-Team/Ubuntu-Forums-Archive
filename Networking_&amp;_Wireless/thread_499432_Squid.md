---
title: "Squid"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by fazavon on 2007-07-12
Okay, I am going crazy here. I have squid installed and working...well kind of. I have three NIC's in the box.

eth2 is external (public ip address)
eth1 is internal (for like six machines)
eth0 is internal (only for wireless)

Now the issue I am having is, I can not ping either internal card. one is a 192.168.131.1 and the other is 172.16.40.1. None of the clients can ping either card nor can either cad ping the clients. 

eth1 ip 192.168.131.1
I have a client hooked up to it via crossover can no ping it.

eth0 ip 172.16.40.1
I have a client hooked up via a switch with an address of 172.16.40.201 can not ping.

I know what you are thinking.. i have two bad NIC's .... No, if i move the external to any of the NIC's they work, I can browse the net, down load updates, pull email from my pop3 account everything works. 

Any help would be nice 

thanks

//j

---

### Post by spd106 on 2007-07-13
What does your routing table look like?
```
ip route
```

Have you blocked icmp/udp in the firewall?

---

### Post by fazavon on 2007-07-20
I got it. It was the nic card. It was going out, but no one told me, they just handed it to me... and then laugh

JERKS!!!

oh well...

thanks for the reply

---

### Post by jortz on 2007-09-20
hello there, soory to bother you but can you help me how to configure squid, eth0 to public then eth1 to lan, how to do that..? help plis  sir...

---

