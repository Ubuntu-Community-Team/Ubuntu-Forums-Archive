---
title: "Access Modem behind Router"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Raan03 on 2008-04-30
Hi

I am experiencing difficulties while I want to browse to my modem's accesspage behind a router.

I have 2 networks at home:

1 Wireless network (router), set with a DHCP-range of 192.168.0.2 'till 192.168.0.255 and the getaway 192.168.0.1 (this page)

And a second "network", a Speedtouch 510, set with a DHCP-range of 192.168.1.64 'till 192.168.1.253 (or so) and getaway 192.168.1.254. it gives a DHCP spoof at 192.168.1.64 (so that that IP will recieve the internet connection's IP)

both will recieve the DNS'ses automatically, in my router's configuration table; I see three DNS'es, the one of my Speedtouch 510 (10.0.0.138 = alternate address for 192.168.1.254) and 2 DNS'es of my ISP and as IP I see my internet connection's IP.

Now the problem is, I cannot access the modem (speedtouch 510) while connected through the router (wireless), gives me some "time out". I am currently using a cable to connect between PC and router and I've untouched the settings in Ubuntu, so that means he 's still in 'roaming mode (?)'.

Any one that can help me? It 's a small problem, but sometimes I need the modem's configuration badly...

P.S. On a "Windows XP", with DHCP enabled he is able to access the modem's page, which makes me think the problem should be at Ubuntu's side? The only difference I think is that Ubuntu's using a cable while XP is using wireless (cable is too short to test XP with cable)

My regards
Ranu

---

### Post by SpaceTeddy on 2008-04-30
can you please draw a picture of your network and how the things are connected with what IP addresses. I can't really follow your explanation... it does not make much sense to me.

Also, If your modem answer on one network, and not on the other, i would think this to be a routing or firewall problem. Either your modem does not know where to find the second subnet, thus the replies from the modem do not get back to your ubuntu box, or your ubuntu box has some firewall installed that blocks the answer...

but without understanding what your network looks like, i cannot help you... sorry :(

---

