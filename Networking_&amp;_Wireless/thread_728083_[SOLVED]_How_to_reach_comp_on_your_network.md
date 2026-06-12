---
title: "[SOLVED] How to reach comp on your network?"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-03-18
Here is the configuration:

--internet--> (eth0)comp1(eth1)-----comp2
------------------(eth0)comp1(eth2)-----comp3.
To explain, my comp1 is connected to internet, and comps2 and 3 are connected by lan to comp1.

Let's say that I have account on no-ip or dyndns, and address of comp1 is: comp1.no-ip.info. When I want to connect to comp1 via ssh then I write in console: ssh [email]username@comp1.no-ip.info[/email] and I connect.
But how do I connect to comp2 and comp3 via ssh (external address is the same)? If I make 3 accounts on no-ip or dyndns, I also get connected to comp1 because noip/dyndns sends external IP of my comp connected to ISP.

---

### Post by Eiríkr on 2008-03-18
As far as I understand it, your DynDNS setup can **only** point to the external IP through which your home LAN is connected to the internet.  As such, you can currently only ssh from outside your LAN into comp1.  The two workarounds are to:
[list][*]ssh into comp1, and from there ssh into comp2 or comp3
[*]set up port forwarding on comp1, so say port 11112 on your external IP is forwarded to port 22 on comp2's internal IP, while port 11113 on your external IP is forwarded to port 22 on comp3's internal IP[/list]

Cheers,

Eiríkr

---

### Post by ene_dene on 2008-03-18
> **Eiríkr said:**
> As far as I understand it, your DynDNS setup can **only** point to the external IP through which your home LAN is connected to the internet.  As such, you can currently only ssh from outside your LAN into comp1.  The two workarounds are to:
[list][*]ssh into comp1, and from there ssh into comp2 or comp3
[*]set up port forwarding on comp1, so say port 11112 on your external IP is forwarded to port 22 on comp2's internal IP, while port 11113 on your external IP is forwarded to port 22 on comp3's internal IP[/list]

Cheers,

Eiríkr
Thanks, this will work. I though that maybe there was some way to do it, like ssh [email]username@comp2.comp1.no-ip.info[/email] or something like that.

---

### Post by Eiríkr on 2008-03-18
Glad to hear that'll work for you.  :D  If this resolves your issue, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  

Cheers,

Eiríkr

---

