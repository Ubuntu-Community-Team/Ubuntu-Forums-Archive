---
title: "removing the proxy in synaptic"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Prakash Premkumar on 2010-06-12
Hi guys, i was using a wifi network in my college..for which i used a proxy.. now i'm back home and am using the broadband connection.. when i try to install packages via ..synaptic it pops with an error saying.. it cannot connect to the proxy "172.16.1.5:8080".. yes of course it should not be able to.. i've changed the settings to direct connection in preferereces/network ... then .. i configured the /etc/apt/apt.conf file..
changed it to  
 Acquire::http :: proxy "false"; .. but i'm still getting that error.. pls help me

---

### Post by Prakash Premkumar on 2010-06-12
[QUOTE=Prakash Premkumar;9451272]Hi guys, i was using a wifi network in my college..for which i used a proxy.. now i'm back home and am using the broadband connection.. when i try to install packages via ..synaptic it pops with an error saying.. it cannot connect to the proxy "172.16.1.5:8080".. yes of course it should not be able to.. i've changed the settings to direct connection in preferereces/network ... then .. i configured the /etc/apt/apt.conf file..
changed it to  
 Acquire::http :: proxy "false"; .. but i'm still getting that error.. pls help me

---

