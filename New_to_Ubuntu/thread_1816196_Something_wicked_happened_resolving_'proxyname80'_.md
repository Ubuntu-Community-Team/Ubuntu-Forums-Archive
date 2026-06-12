---
title: "Something wicked happened resolving 'proxyname:80' (-5 - No address associated)"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by snigam3112 on 2011-08-01
i am accessing the net thru a proxy server provided by my college.
I can get synaptic to work by giving my proxy details in synaptic's prefernces.

using sudo apt-get update and similar orders, i was getting the 407 proxy authentication required error.

this is i fixed by editing /etc/bash.bashrc and /etc/apt/apt.conf

now i am getting the following error on running sudo apt-get update:

...
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
  Something wicked happened resolving 'proxyname:80' (-5 - No address associated with hostname)
...

using ubuntu 11.04

what should i do?

---

