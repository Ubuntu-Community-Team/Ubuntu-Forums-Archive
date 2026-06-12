---
title: "vpnc with IKE and ca-file support"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by SpaceTeddy on 2007-11-08
Hi Everyone,

this is starting to piss me off. I study at two universities, and both of them use the Cisco VPN client. Now, scold me or not, i don't like their client. So, here i am trying to setup vpnc.

Uni 1: 
I copy/modify the supplied config file to /etc/vpnc/uni1.conf punch in sudo vpnc uni1 and it works like a charm. Except for the fact that i get kicked out about every hour... but ok, that happens and i can live with it. 

Uni 2:
I do the same thing, I copy the config file (this time they have a certificate too), get the certificate, copy it to the right places, set the paths in the config... and vpnc tells me that the directives ca-file and IKE are unknown... and i don't know why... 
**really i am at loss.** 
I have tried to compile vpnc myself (I can't even get the openssl Support to work due to fact that there is no ./configure in the source) and every time i try it tells me those directives are not supported or i have no openssl support... 

Now some information about the Configs:
here is my config file:
> IPSec ID hybrid-default
IPSec XXXXXXXXXXXXXXXXX
IPSec obfuscated secret XXXXXXXXXXXXXXXXXXXXXX
IKE Authmode hybrid 
ca-file /etc/vpnc/rootcert.pem
Cisco UDP Encapsulation Port 14195
Xauth username XXXXXXXXXXXXX
Xauth password XXXXXXXXXXXXX

I have replaced sensitive data with XXXXXXXXXXXXXX.

when i run this thing it tells me:
> vpnc: warning: unknown configuration directive in /etc/vpnc/zedat.conf at line 4
vpnc: warning: unknown configuration directive in /etc/vpnc/zedat.conf at line 5

which is the ca-file and the IKE... and i don't know why. since the uni acctually supplies this as a configuration file for vpnc, i thought it would work... well,i doesn't. it sits there for a while, and then disconnects itself.

can anyone help me with this... tell me how to compile the 0.5.1 with openssl support, or how i can get those two lines to work... please...

thanks a lot in advance

---

