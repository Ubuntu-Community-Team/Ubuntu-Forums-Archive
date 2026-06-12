---
title: "Problems with port 22: No route to host"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by nanditha.ec on 2013-11-23
Hi

I have a strange problem here.
I have ubuntu 12.04 running on my laptop. I am behind a proxy and am trying to ssh to an external machine (which I guess, connects over internet.. Its IP reads: yuva.cdac.in )

When I connect, this is what I see:

nanditha@nanditha-vaio:~$ ssh -vv [email]nanditha@yuva.cdac.in[/email]
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to yuva.cdac.in [196.1.113.96] port 22.
debug1: connect to address 196.1.113.96 port 22: No route to host
ssh: connect to host yuva.cdac.in port 22: No route to host


where as, when I ssh to a different machine in my lab in the same campus, it gets connected from my laptop. So, there is no problem with ssh as such.
Also, if I connect to yuva.cdac.in from my lab machine (which is again, behind the same proxy), it works.. So, it has nothing to do with proxy obviously.

And.. if I connect from my laptop, through a wireless broadband connection (which is not behind any proxy), it connects from the very same laptop.. So again, nothing to do with ssh and no need of reinstalling ssh etc.,

I am not sure how to debug this thing.. Any help is appreciated.
And.. I had this working on my laptop, in my old hard disk which crashed.. I had to buy a new one and install ubuntu.. and the issue is being observed on this newer one.. (although, this information might be really useless to debug my case)

Thanks
Nanditha

---

### Post by bashiergui on 2013-11-24
Can you ping the address?
Check with the proxy administrator to see if they allow outbound connections to port 22. 
Also check that you don't have a firewall enabled on your computer that is blocking the connection.

---

