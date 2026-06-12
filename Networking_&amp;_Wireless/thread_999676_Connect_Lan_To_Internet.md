---
title: "Connect Lan To Internet"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by GenesisV2.0 on 2008-12-02
Hi 

Basically i have set up a python firewall script that is running on a sepearate box that allows inbound connections on port 21 to a server in my lan. But i want to be able to connect me computers from the lan to the internet through this phyton box - it has two nic cards 1 connected to the hub of my lan and the other is connected to the internet - i just need to forward port 80 on the lan card to the internet and pass it back - i have tried squid but the configuration said nothing about two nic cards and the massive conf file was beyond me - i just want to use that computer as a gateway to the internet for the computers connected to my lan - aka use ti as a web proxy.

cheers
adam

---

### Post by SpaceTeddy on 2008-12-02
A gateway does packet forwarding. It does now care about what kind of packet it is, and it does not care what protocoll or content is carried. Gateways act on the IP layer. Keyword: "[[COLOR="Blue"]Internet sharing[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874")" !

A Proxy relays connections. For this, it accepts a connection to a client, then puts up it's own to the server specified by the client and relays that information between the two. If the content of the connection is not enctypted/secured, proxies might also cache, manipulate or redirect. Proxies work on the application layer and do not work for all connection types - only for those a proxy was written for. 

which one if the two do you want ?

PS: Of course, it is possible to have both at the same time - but since squid was already lots for you, i'd say you want something simple (although, there is really nothing that simple).

---

