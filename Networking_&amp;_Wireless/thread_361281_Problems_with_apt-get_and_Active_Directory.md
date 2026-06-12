---
title: "Problems with apt-get and Active Directory"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by danielprice on 2007-02-14
Hi, we've recently set up a machine running Ubuntu 6.06 on our (windows, AD) network here. We've no real need to get users authenticated using AD or LDAP, but we do need to be able to access the internet. 

I've got the machine set up on the network and browsing shares fine, we can access the internet through the ISA proxy server, but what's getting me is using apt-get. 

Every time I try to use it, I get a 407 Proxy Authentication needed error. The same happens using synaptic. What gets me is that there's no way to enter user information into these programs. 

I've edited /etc/apt/apt.conf to include the http_proxy line, done the same to /etc/bash.bashrc, and I've tried exporting it from the command line. I've been putting it as http_proxy=http://DOMAIN\\myuser:mypass@myproxy:myport and [http://DOMAIN\myuser:mypass@myproxy:myport](http://DOMAIN\myuser:mypass@myproxy:myport), every time it comes up as a 407 proxy authentication required. Querying the ISA server shows that none of these have passed the username to our ISA proxy, so the requests were denied for trying anonymous access.
Any clues?

---

### Post by jkeyes0 on 2007-02-14
We use Proxy server (pre ISA server) here at work, and I've found that it works using NTLMAPS ([http://sourceforge.net/projects/ntlmaps](http://sourceforge.net/projects/ntlmaps).)

I used the tutorial found [here]("http://www.tuxmachines.org/node/12889/print")

Hope this helps.

---

### Post by furtherdream on 2007-12-17
Hey, jkeyes0
Thanks for your information, i just got access to internet with ntlmaps. Very good, i can get update in my office now. many thanks.
:)

---

