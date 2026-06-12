---
title: "Port Redirecting"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by dcomsa on 2007-06-04
Hi everyone,

What I would like to achieve (and didn't succeeded yet) is to redirect a tcp package to another machine. Please note that this is NOT for nat and translating between two networks (internet+private). 

Basically, what I want is: 
- all connections coming on one specific port to be redirected to another ip address;
- both addresses are real (public) ip addresses;

For instance, if i make:

# telnet 84.34.56.34 55555 (from some machine)

then the server at 84.34.56.34 should redirect the request to 210.234.23.22 on port 33333.

Is this possible? (ip addresses used above are fictional)

Thanks,
Daniel.

---

### Post by cornsnap on 2007-06-04
There is an application you can download called redir

apt-get install redir

syntax
usr/sbin/redir [options] [remote-host] listen_port connect_port

Try this I've never used it but heard of it.

---

### Post by dcomsa on 2007-06-05
hi cornsnap,

thanks for your reply. i think i'll try the app you suggested. but i was hopping on an answer based on iptables. does anyone knows if this could be done using iptables?

thanks,
daniel.

---

