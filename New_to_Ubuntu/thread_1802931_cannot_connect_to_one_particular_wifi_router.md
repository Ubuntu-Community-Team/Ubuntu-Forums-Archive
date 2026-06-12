---
title: "cannot connect to one particular wifi router"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by titusDT on 2011-07-12
Hi all

   I am experiencing difficulties connecting to one particular wifi router called Baltus i.e. :
- i can connect other wifi routers
- from another laptop i can connect to Baltus
- from my laptop connection fails.

I checked that I have the right password and the right security type (WEP with password). 

I have no skills in wifi interface configuration/troubleshooting. Anybody can help ?

cheers
gus

PS like those smileys you got there on the forums
:popcorn::):P:(:confused::guitar::lolflag:

---

### Post by smurphy_it on 2011-07-12
You should login to the web interface for the router.  It may only be letting "specific mac addresses" to connect.  Additionally, it may only allow newer modes to connect.  So for instance, you could connect with a wireless G or Wireless N, but not with wireless a or b.

---

### Post by titusDT on 2011-07-13
I dont have access to the interface the router is owned by the landlord whos on vacation ... bummer. Anyway since the whole building is using that router seems weird that one additional cpu out of 20 should not be able to connect. 

Any way I ll make do with it until the landlord returns and restart this thread then.

Thanks for the reply anyway !

---

### Post by Peter09 on 2011-07-13
Try going to network manager - right click and select the edit connections tab and find the relavent wireless access point specification. Delete it. Now try and connect to the router again - it may work.
 
I had a similar problem. I bought a new router and set it up exactly like the old one - but entered the SID in uppercase. Everyone (running linux) could see the interface but could not connect - it needed to be deleted to allow things to start again.

---

