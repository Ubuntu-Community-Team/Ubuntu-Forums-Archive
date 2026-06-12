---
title: "Why Do i need a DCHP Server"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-01-08
Hello some people have been telling me that i should make my file server a dhcp server as well.
I asked them Why? They said it assigns ips to the computers. I though what is the need when on the windows and ubuntu computers i can just set the ip address there.
My current setup is 2 ubuntu client computers a windows laptop and a ubuntu file server.
So what is the advantage.

EDIT: woops i wrote dchp server instead of DHCP.

---

### Post by linuchsan on 2007-01-08
What people say, if you don't have rights to change your ip to static.
Sample, if you would have 100 clients or more, and some settings are changed, like dns settings, it is handy to have a dhcp server, or if you like to walk much and have time for it to change all the client settings by hand :-)
But for you, don't bother.

---

### Post by CameronCalver on 2007-01-08
well at the moment my mum has a laptop and she uses it at home and at work but at home the network is 192.168.1.1 and at work it is 192.168.0.1 and if i set roming ip there is heaps of ip conflics and it stuffs everything up so thats why i need it

---

### Post by linuchsan on 2007-01-08
that is an other sample...yes. Did you have some problems setting it up?

---

### Post by CameronCalver on 2007-01-08
Setting What up?

---

### Post by seuaniu on 2007-01-08
Static IP is an easy way to go for small networks... but what happens when things change or one of your buddies comes over with his laptop?  DHCP to the rescue!  Really, for small networks, the only advantage is to not have to ever configure more than one thing when your network changes (dns, etc).  Its easy and quick to set up, and when mom comes over to get her computer fixed, its one less thing that you have to configure.

---

### Post by CameronCalver on 2007-01-08
Yeh i have friends over all the time and iis annoying to set up thats why it would be good just connect to the network and he has an ip

---

