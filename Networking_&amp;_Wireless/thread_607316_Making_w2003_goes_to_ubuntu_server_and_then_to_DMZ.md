---
title: "Making w2003 goes to ubuntu server and then to DMZ"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by LMSSML on 2007-11-08
Hi people !

I wanto to having all traffic goes to linux and respective firewall.

Is it possible configure ubuntu server has a gateway and then in linux server configure the ip to goes to dmz  ?

And if the awnser is affiramtive where in Linux could I chanbe that ?

---

### Post by mpierce on 2007-11-08
You can do what you want if your server has two nic cards installed and it is not easy as I use to run this type of setup. If you are using a router with multiple ports, it is probably best to allow it to be the dhcp server and use it's firewall rules. 

If you persist, the server will have one card setup to allow connections to it and the other card has to be setup for internet access and as the gateway.  You'll also have to setup firewall, e.g., Shore or some other and a dhcp server.

Hope this helps...

---

### Post by LMSSML on 2007-11-08
I've a dhcp server in ubuntu.

I've got a router that is configured to be a DMZ and then what I wanto to do it's having all internet traffic goes to server then be distributed to the other pc's.

---

### Post by mpierce on 2007-11-08
If you are using a 1-nic server with a router, you cannot do what you want to do. You need 2 nics.

---

### Post by LMSSML on 2007-11-09
Now I've got two nics and how it can be done, I've tried to configure firestarter with second nic but it says that my internet it's not available.

Could anuyone help

---

