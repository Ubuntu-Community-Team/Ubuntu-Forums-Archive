---
title: "Best solution work/home remote"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by rcmn on 2007-08-27
I have been exploring a lot of solutions for accessing my home network from work but i have been unsuccessful so far.
My home network is very simple (internet)<---->[Modem] <==> ||firewall/DHCP||>>>nodes
I have a total control over it no problem.
Now the kicker work:
(internet)<---->{DMZ  [Modem] <==> ||firewall|| } <==> Proxy <==> web browsers

So i can only use web browsers to access internet.I tryied to use other application with the proxy informations and add my credential information but it won't work...I tryied http tunnelling etc...but i couldn't have it working.

Now my only hope is with the new WebOS like (youOS.com) ajax/flash apps .I wish i could just interact with my local PC throu a solution like this one. 
I tried web console but it required a direct connection 22/ssh ...bummer.

Does anyone have a suggestion ?

---

### Post by rcmn on 2007-09-05
anyone ?

---

### Post by KCPokes on 2007-09-05
Have you tried basic SSH out from your corporate firewall?  Most corporate firewalls will allow SSH (port 22) traffic out, thus once you have that option you can do ALL SORTS of things.  For example, with a simple SSH connection to home I can 1) configure my browser to use my home connection, tunnelling via SSH, to surf the web, thus getting around any blocked sites at work ( Fantasy Football for example), or 2) connect to my VNC server via my SSH tunnel, thus controlling my home machine from work.

There are various things you can do, with a simple SSH connection, but you first need to determine if you can connect.

---

### Post by rcmn on 2007-09-05
That was the first thing i tried but no it's blocked. I even tried to run it from 8080 or 80 but the protocole seems to be blocked as well :'-(

---

