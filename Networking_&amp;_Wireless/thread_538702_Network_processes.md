---
title: "Network processes???"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by notwen on 2007-08-30
I've been trying to find out if Linux or GNOME launches any processes once a connection is established?  I'm wanting to find out if I can relate any certain process specifically to eth0 or eth1(once one of them connects to a network.)?  It would also be helpful to know if there is such a process invoked by achieving a connection, does said process continue to run throughout the duration of the connection?  

If there are no such processes, would it be difficult to have Linux automatically start a dummy process that constantly checks for the active connection and will close once the connection is lost? 

Thanks for any insight or info you may have to offer. =]

---

### Post by noob12 on 2007-08-30
You can probably get what you want following one of these two paths:  

You can use **up** and **down** directives in **/etc/network/interfaces** to run arbitrary commands when the interface comes up and goes down.     See **man interfaces**.

Alternatively you can write a script that just examines a specific interface using **ethtool**, and behaves differently depending on the link state.

---

