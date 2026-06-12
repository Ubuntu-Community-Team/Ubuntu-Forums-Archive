---
title: "DynSite equivalent for Ubuntu?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Bobbafett on 2007-06-26
Hello everybody :)
Is there a DYNSITE ([http://www.noeld.com/dynsite.asp](http://www.noeld.com/dynsite.asp)) equivalent for Ubuntu? I am specifically looking for a equivalent that will run on Edgy.

Thanks

---

### Post by netztier on 2007-06-26
> **Bobbafett said:**
> Hello everybody :)
Is there a DYNSITE ([http://www.noeld.com/dynsite.asp](http://www.noeld.com/dynsite.asp)) equivalent for Ubuntu? I am specifically looking for a equivalent that will run on Edgy.

Thanks

entering "dyndns" as search keyword in Synaptic lists a few packages - where **ddclient**, **ddns3-client** and **ez-ipupdate** seem most appropriate - maybe together with **ipcheck** which can help determine your "outside" IP address if you have a router or firewall between your PC and your broadband connection. 

Sometimes, these devices implement DDNS clients themselves, be sure to check! It's a lot more comfortable than installing a DDNS client on your PC.

best regards

Marc

---

### Post by Bobbafett on 2007-06-26
Thanks! I'll check those out.
Also I ran into a product called No-IP on this page: [http://www.no-ip.com/downloads.php](http://www.no-ip.com/downloads.php) which seems to have the same functionality.
Anyone has used any of these programs? which one would you recomend?

Thanks

---

### Post by t4thfavor on 2007-06-26
i use no-ip.com, for the client though I use whatever comes on the ipcop firewall distro. Also most routers have this capability built in now, it may be easier to config your router (if you have one).

---

### Post by kevdog on 2007-06-26
I too use noip.com.  Although it is easier to configure on your router (thanks for tip above) if you want to configure it the traditional way the do offer a dynamic update client that works with linux!

---

### Post by Bobbafett on 2007-06-26
Through the router? I'll have to check that out once I come back home.
I am sure my LinkSys router has a port forwarding section, in which I can re-route specific requests to different machines in my network, but I am not sure I have seen a Dynamic DNS feature in there :-k

---

### Post by az on 2007-06-26
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by zildian143 on 2008-05-01
im using dyndns.org in a ddns3-client. but im having error on connecting through port 5000. hope you can help me. thanks

error message:
Setting Dynamic DNS v3: philserver.serveftp.net IP at dyndns.org unchanged,
connect(): Connection timed out
server_message: dyndns.org:5000client_error: could not connect to dyndns.org:5000, exiting

---

