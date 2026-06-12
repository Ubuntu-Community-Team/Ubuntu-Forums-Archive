---
title: "No connection from different subnet"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by sebastian_b on 2008-11-17
Hello there.

The situation is as follows:
I tried to set up a server at a friends place with direct connection to a university network. I also have access to this network through vpn. What i want is a connection from my place through the vpn tunnel to the server.

Although the same setup used to work with a windows machine it does not with the new server (ubuntu 8.4 server edition).

The network (as far as i can tell) has the following structure: my friend is located in a tiny subnet containing 5 or so ip adresses with the form 10.148.245.15x (netmask is 255.255.255.248) he has a gateway to the "big net" and can reach all other adresses within the 255.0.0.0 university subnet as well as the internet from there.
When open a vpn tunnel i get an ip 10.x.x.x which is reachable from the small subnet.
The server located at the small subnet is reachable from within there (ping, ssh, everything else i tried). It has the correct gateway and dns server installed (confirmed simply by pinging [www.heise.de](www.heise.de) from the server). However, while i am able to ping my friends desktop computer through the vpn tunnel this does not work for the server.

So this seems to me like the server rejects packets coming from a different subnet. But i could not find a place where to change such a behaivour. Also as long as this server was standing behind a DSL router it was reachable from the internet (using port forwarding at the DSL router).

The problem is that i do only have one more chance to install the server at this place before i leave the country for a longer time.

The server is currently located back in my home network so i have full access but can not easily reproduce the situation in the university network 

I would be very glad for any proposals on where this behavior comes from or how i could do any troubleshooting.

---

