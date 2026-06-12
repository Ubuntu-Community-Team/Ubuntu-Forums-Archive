---
title: "Why is there traffic in TCP 0?"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by cgr1fatboyslim on 2006-10-17
I'm just wondering how come **firestarter** seems to block unwanted traffic e.g. TCP 20,while **iptraf** seems to indicate traffic passing thoughs ports.This happened when I visited auditmypc.com and tried the firewall test, and there appeared to be traffic TCP port 0? and TCP 20?(although firestarter says it blocked it). Also wondering **how can I make my browser/box/OS more stealthy?** Auditmypc seemed to know what my browser,operating system,size of my screen?,who knows what else.

---

### Post by tturrisi on 2006-10-17
The info about your computer settings is passed in the browser headers when requesting a doc on a www server.  The only way to stop that is to use a proxy server that spoofs the browser headers.  These headers are a necessary part of tcp/ip networking (Internet Protocol).

---

### Post by cgr1fatboyslim on 2006-10-22
Hi Thanks for your reply.I was wondering is there any thing i can do to make my box more secure even if it is a stand alone dial-up machine? i've been trying to learn how to configure my iptables without the GUI(Firestarter),i would like to use only use remote ports TCP 53,80,123,443(surf the net,check mail and have accurate time)...i'd greatly apprciate it if you could advice me on how to only allow traffic to these said ports that i use,and then drop/block the rest of the ports from 1 to 65535 UDP/TCP/ICMP/etc and of course drop all incomming packets(traffic)...hoping for your kind advice on the matter...thank you in advance:)

---

### Post by tturrisi on 2006-10-22
You cannot use the wwww, p2p, etc and block all those ports!
First of all, your comp will never use port 80 unless you run a www server.  The browser does not use port 80.  It may send a request to port 80 on a ww server & the server will send back on unassigned tcp ports, beginning with something like 1024 + up.  Port 53 is for a nameserver, and again, when browsing the www you are using port 53 on a server, not your own port 53.  Clients (browser, email, p2p, time, etc) do not use those ports.

No need to get that into security w/ dialup anyway.  Your ip changes each time you connect.  Someone else may have more to say, I never use any software based firewalls on any of my home systems, just a router w/ nat is plenty.

---

### Post by cgr1fatboyslim on 2006-10-23
I know what u mean TCP 80,53,443,123 are the remote ports on the www servers & in turn will send back to my dynamic tcp ports...lucky you've got a router...I anm hoping to purchase a couple of old pc's to set up a little home network too...so what brand of router would you recomend?By the way I tried your advice on the proxy stuff,but I some how was unsuccessful in configuring privoxy and tor...kinda gave up on it for now...thanks for your info

---

