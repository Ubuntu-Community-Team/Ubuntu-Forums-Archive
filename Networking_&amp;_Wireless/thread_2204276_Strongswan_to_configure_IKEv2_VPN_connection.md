---
title: "Strongswan to configure IKEv2 VPN connection"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by scudelari on 2014-02-07
Hello Everyone,

I am trying to configure a VPN connection from my UBUNTU server to my windows 2012 server. The windows server controls VPN connections and I am able to connect using windows 8 clients.

In my UBUNTU server, I can access the network manager and I can create using the user interface a new VPN using PPTP. 

I must use the protocol IKEv2, which is handled by strongSwan. 

I installed, as it is said [here]("http://wiki.strongswan.org/projects/strongswan/wiki/NetworkManager"), the network-manager-strongswan package. After I installed, when I add a VPN connection I have the option now to select the strongSwan option.

But when I hit CREATE, the interface hangs. The Create button is kept pressed and the interface hangs. Nothing happens anymore.

What could I do? If at least someone could tell me which logs to check.

Thanks a LOT!

---

### Post by scudelari on 2014-02-09
Noone?

---

### Post by mariogar1001 on 2014-04-09
> **scudelari said:**
> Hello Everyone,

I am trying to configure a VPN connection from my UBUNTU server to my windows 2012 server. The windows server controls VPN connections and I am able to connect using windows 8 clients.

In my UBUNTU server, I can access the network manager and I can create using the user interface a new VPN using PPTP. 

I must use the protocol IKEv2, which is handled by strongSwan. 

I installed, as it is said [here]("http://wiki.strongswan.org/projects/strongswan/wiki/NetworkManager"), the network-manager-strongswan package. After I installed, when I add a VPN connection I have the option now to select the strongSwan option.

But when I hit CREATE, the interface hangs. The Create button is kept pressed and the interface hangs. Nothing happens anymore.

What could I do? If at least someone could tell me which logs to check.

Thanks a LOT!

Hi,

Long time has passed since your post but I'm fighting with this right now.


I had the same problem you mentioned above and the workaround was to remove the network-manager-strongswan package installed via apt-get.
After removing it, I had to build it from source code as explained [here]("http://wiki.strongswan.org/projects/strongswan/wiki/NetworkManager").

The Network Manager should work after doing that.


Regards.

---

