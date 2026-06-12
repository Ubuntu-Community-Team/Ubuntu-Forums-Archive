---
title: "is firewall needs to be configured after a fresh install of ubuntu?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-22
hi!
Well i have just installed ubuntu.
So I would like to ask that do I need to install a firewall manually or it is configured by default under ubuntu?
Like anyone can trace my ip address through nmap or some other tools if my firewall is not configured.
Thanks!

---

### Post by mike555 on 2010-07-22
I recommend you install " GUFW " , it will let you easily turn on your firewall .... no real need to configure it , just turn it on ...

---

### Post by mcduck on 2010-07-22
Linux itself includes all the necessary tools and components to create a firewall, but the default install of Ubuntu doesn't have any firewall running as it's not required. The default setup has no running services that would respond to incoming connections from network, which means that a firewall wouldn't have anything to do. If nothing is listening to a port, there's no need to close the port either.

If you really want to, you can of course set up a firewall. In that case I recommend Gufw for handling the firewall configuration for you (although if you aren't afraid of command-line then UFW is a really simple firewall configuration tool and it's included by default. Simple "sudo ufw enable" in a terminal should do the trick for most users.)

edit:
"Like anyone can trace my ip address through nmap or some other tools if my firewall is not configured."
They would actually need to already have your IP address to do any scanning (unless you are talking about a local network, not the Internet), and the NMAP scan would only tell them that no ports are available for connecting (unless you have yourself installed some server application that would listen to a certain port).

---

### Post by louieb on 2010-07-22
Your really don't to mess with the firewall - a default install does not listen to any ports. IPTABLES is the default firewall - things iike GUFW and firestarter just offer a GUI to write IPTABLE rules. 

If you visit a website or use some ftp server ... lol ... if you use the Internet at all -   the server(s) you visit knows your IP  - your machine has to sent it  -  if they didn't - you could not get a reply. I suppose you could use some proxy server - if hiding the IP is important to you. - But that has nothing to do with the firewall.

---

