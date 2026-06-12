---
title: "does ettercap work as a packet sniffer ?"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-07-17
hi all,
I was working on a cyber security demo, a few days back.
I wanted to show how easy it is to sniff the username and password alongwith the website on the LAN, using ettercap. I used ettercap Graphical and had enabled the packet forwarding option using the following command before starting ettercap.

      [I][B]sudo echo "1" >  /proc/sys/net/ipv4/ip_forward

[/B][/I]I succeed in arp poisoning all the hosts and can see the connections in the view connections and profile tabs. The output is as under :-
[I][B]ARP poisoning victims:

 GROUP 1 : ANY (all the hosts in the list)

 GROUP 2 : ANY (all the hosts in the list)
[/B][/I]
But beyond that it doesnot work ?! I have lib3 failures which read as under :-
[COLOR=Red][B][I]SEND L3 ERROR: 28 byte packet (0800:01) destined to 10.0.0.3 was not  forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not  permitted) 
) [/I][/B][/COLOR]

Can someone guide me through it ? 
thanks
nishith

---

### Post by haqking on 2011-07-17
> **nkdnkd said:**
> hi all,
I was working on a cyber security demo, a few days back.
I wanted to show how easy it is to sniff the username and password alongwith the website on the LAN, using ettercap. I used ettercap Graphical and had enabled the packet forwarding option using the following command before starting ettercap.

      [I][B]sudo echo "1" >  /proc/sys/net/ipv4/ip_forward

[/B][/I]I succeed in arp poisoning all the hosts and can see the connections in the view connections and profile tabs. The output is as under :-
[I][B]ARP poisoning victims:

 GROUP 1 : ANY (all the hosts in the list)

 GROUP 2 : ANY (all the hosts in the list)
[/B][/I]
But beyond that it doesnot work ?! I have lib3 failures which read as under :-
[COLOR=Red][B][I]SEND L3 ERROR: 28 byte packet (0800:01) destined to 10.0.0.3 was not  forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not  permitted) 
) [/I][/B][/COLOR]

Can someone guide me through it ? 
thanks
nishith

I dont know what others think but this is not a Pen testing forum, supporting use of MiM attacks i am sure is not at the top of the list here.

Also you want someone else to show you what is wrong with something you want to use to show others how easy it is ?

try here [http://linux.die.net/man/8/ettercap](http://linux.die.net/man/8/ettercap)

---

### Post by gandaran on 2011-07-17
> **nkdnkd said:**
> hi all,
I was working on a cyber security demo, a few days back.
I wanted to show how easy it is to sniff the username and password alongwith the website on the LAN, using ettercap. I used ettercap Graphical and had enabled the packet forwarding option using the following command before starting ettercap.

      [I][B]sudo echo "1" >  /proc/sys/net/ipv4/ip_forward

[/B][/I]I succeed in arp poisoning all the hosts and can see the connections in the view connections and profile tabs. The output is as under :-
[I][B]ARP poisoning victims:

 GROUP 1 : ANY (all the hosts in the list)

 GROUP 2 : ANY (all the hosts in the list)
[/B][/I]
But beyond that it doesnot work ?! I have lib3 failures which read as under :-
[COLOR=Red][B][I]SEND L3 ERROR: 28 byte packet (0800:01) destined to 10.0.0.3 was not  forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not  permitted) 
) [/I][/B][/COLOR]

Can someone guide me through it ? 
thanks
nishith
if you are trying to capture SSL encrypted usernames and passwords (HTTPS connections) you will have to use SSLStrip together  with ettercap, you will have a lot to learn, google the subject.

---

