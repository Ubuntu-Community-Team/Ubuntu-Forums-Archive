---
title: "hostname based routing"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by cdmdotnet on 2008-04-21
I've got a situation where i am only assigned one static public IP from my ISP, however I have a need for routing based upon the hostname within a packet (mostly for web traffic, IE two development web servers not in a load balanced situation)

I cannot use separate public ports (IE 80, 8090) as the main users of these servers are in corporate environments where they have strict rule on their proxy / firewalls that will not allow any non standard ports.

I know i can do this with hardware equipment, but i'm wanting to know if there is something for linux / ubuntu that can do this. I imagine it's not much more then NAT but looking at hostnames as well as port.

any ideas guys?

---

### Post by SpaceTeddy on 2008-04-22
routing works (as far as i know) plainly on ip's. there is no way you can decide upon the content of the paket where to send it with a routing decisison or paket filter rule. They don't even consider the TCP payload, let alone scan it and then act on it.

However, maybe you should have a look at apaches mod_proxy. Installing that on the machine which does the decisison, you can then tell the apache there to forward the requests to the specific servers upon a request to a spcific hostname you are connecting to. Of course, the CPU cost is higher than the routing one, but at least this should work... i think

that is about the closest thing i can think of what would do the trick... 
hope it helps :)

---

### Post by cdmdotnet on 2008-05-24
thanks for that SpaceTeddy. I've finally got apache_proxy setup and working pretty sweet. 

I now have an odd and tricky SSL issue to try and solve. I'm aware that with HTTPS the host headers are inside the encrypted packets. All that is not encrypted that is useful is IP and port. Now since i have an issue where I've got to try and allow two different SSL / HTTPS certs to work on the one IP and one port.

I've discovered that there is a Connect process that happens in plain HTTP (non encrypted), there is the rewrite engine in apache and as far as i can tell I've ended up with a situation with my SLL / HTTPS communications that resembles (I've figured this since i've installed certs on the apache machine that are in use as the cert delivered is different from the cert used to talk to the back end servers)

    User <-- SSL --> Apache decrypt and re-encrypt <-- SSL --> server

now i'm wondering if anyone has any highly intelligent ideas on how i could mangle with the rewrite engine to send the request to the correct backend server from apache. A nice and transparent solution?

IE

[HTTPS://domain1.com](HTTPS://domain1.com) > apache_mod_proxy / rewrite engine -> [https://internalmachine1](https://internalmachine1)
[HTTPS://domain2.com](HTTPS://domain2.com) > apache_mod_proxy / rewrite engine -> [https://internalmachine2](https://internalmachine2)

---

