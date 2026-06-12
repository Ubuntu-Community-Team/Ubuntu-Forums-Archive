---
title: "SSH Remote Login"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-02-16
How does one find out what the IP address is for your machine to remotely log in using an SSH connection?

---

### Post by cariboo on 2010-02-16
Where are you trying to access the server from, if it's just inside your local network, setup a static ip address on the server. If you are try to access the server from outside your local network use something like dndyns or no-ip and access using the url you chose when setting up either service. 

You will still need to set up a static ip address for the server for port forwarding.

---

### Post by HermanAB on 2010-02-16
Howdy,

To see your IP address, you could hover your mouse over the network thingy, or you can run /sbin/ifconfig.

---

### Post by switch10 on 2010-02-16
or
```
 ifconfig 
```

---

### Post by freak42 on 2010-02-16
If you want to access your home computer from outside our home, and your ip adress changes (often) then you might want to setup dynamic dns, it's free for instance at this site:
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

hth

---

### Post by baddnady23 on 2010-02-16
Thank you, I will go on what you guys are saying here and see where it gets me

---

### Post by baddnady23 on 2010-02-16
ok so once i have my url chosen through dyndns, how to i go about accessing the remote machine with it using the "Connect To Server" application?

---

### Post by freak42 on 2010-02-17
you simply use your dyndns url wherever you would have used the machines ip adress.

some pitfalls:
*do you have your router or computer setup to automatically update dyndns with the correct ip?
* if you have a router/nat/firewall you most likely need to setup port forwarding so that your (ssh) traffic gets routed to your home computer.

---

