---
title: "Problems with a proxy server,I think...."
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by odin on 2005-05-30
Hi everyone!!!

Ok now my problem has changed.I dont know if you read something before but the problem with the proxy it's gone.My problem now is that I dont know why I can use the internet but only with firefox(the browser I have).

The "funny" thing is that if I try apt-get update or install or whatever it doesnt conect to any repository..........

I dont know what to do,any help?


Thank's

---

### Post by fabiand on 2005-05-30
[QUOTE=odin]Hi everyone!!!

Ok now my problem has changed.I dont know if you read something before but the problem with the proxy it's gone.My problem now is that I dont know why I can use the internet but only with firefox(the browser I have).

The "funny" thing is that if I try apt-get update or install or whatever it doesnt conect to any repository..........

I dont know what to do,any help?


Thank's[/QUOTE]
 Hello,

the problem is, that you need to tell various applicstions to use your proxy.
To apt-get something you need to tell apt to use a proxy. The best way to do this, is to use synaptic and enter your proxy informations in the internet dialog in the preferences somwhere.

- fabiand

---

### Post by odin on 2005-05-31
I tried that in synaptic but still doesnt work.

Is there any other application where I have to do the same?

Maybe it is just a security configuration in the proxy....?If it is that then there is no solution,how can i find out?

---

### Post by odin on 2005-07-15
I found the solution for using apt behind the proxy.I post it so everyone who could have the same problem can fix it.

It is as simple as editing  /etc/apt/apt.conf.d/proxy (you probably dont have proxy under apt.conf.d so just create it by editing)

vi  /etc/apt/apt.conf.d/proxy

and then write the following line:

Acquire::http::Proxy "http://your_proxy_IP: proxy_port";

With this I cannot access the ftp repositories but with the rest works fine or it's again a proxy rule that I dont know how to "jump"


Hope it helps for someone :smile:

---

