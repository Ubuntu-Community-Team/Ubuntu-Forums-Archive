---
title: "Ubuntu ignores incoming from WAN"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by danieR on 2007-08-30
Firstly my network setup:
A D-Link DI-524 router connected to a cable modem, one box with Ubuntu connected to the router using an Ethernet cable and a few Windows boxes connected using wireless. All the boxes are defined to receive a preset IP from the DHCP on the router (for example, the Ubuntu box is 192.168.0.101, my own personal computer is 192.168.0.102, etc...)

I've installed Apache and a BitTorrent client on my Ubuntu box and they both ignore incoming connections from the WAN - I can access my website by typing "[http://localhost/]("http://localhost/")" or "[http://127.0.0.1/]("http://127.0.0.1/")" on the Ubuntu box, or by typing "[http://192.168.0.101/]("http://192.168.0.101/")" on any computer in the network.
What I can't do is access it using my WAN IP ("[http://217.132.217.40/]("http://217.132.217.40/")" right now, but this changes once in a while)

I tried port forwarding and DMZing the Ubuntu box on the router without much help - but when I port forward or DMZ my Windows box, it receives connections on 217.132.217.40 (checked with the software firewall logs by trying to fetch a random port with a browser and seeing a refused incoming connection... but at least it means that the computer was reached) - so I doubt it's the router or my ISP

Here are my ***ifconfig -a***, ***sudo iptables -L*** and ***netstat -tnl*** on a pastebin: [http://pastebin.com/m15a6e840]("http://pastebin.com/m15a6e840")

What should be my next step?

---

### Post by dmizer on 2007-08-30
it is not possible to access your wan address from your local network unless you have some sort of complex loop back in place.

i can see your website fine.

edit: and you've got a whole bunch of exposed data on that system.  i suggest locking it down and quickly.

---

### Post by cagey cretin on 2007-08-30
I can get to your site with the [http://217.132.217.40](http://217.132.217.40) address as well. dmizer is right. You're showing stuff you shouldn't...

---

### Post by danieR on 2007-08-30
I guess my previous ISP got me used to this unexpected behavior as I could get to my WAN address from inside my LAN

Thanks for your help and you concern for my security - it's jump temporary measures to help me get used to this new box... I should really delete it now :)

---

### Post by dmizer on 2007-08-30
did your server have a direct wan ip with internet connection sharing with your old isp?

if your web server also acts as your firewall, then it will work.

SOME retail level routers are able to handle wan loopback, but most do not ... or do not do it well.  you may have simply been lucky.

---

