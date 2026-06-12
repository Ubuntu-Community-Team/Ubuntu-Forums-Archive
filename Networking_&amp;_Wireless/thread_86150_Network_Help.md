---
title: "Network Help"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by Crazkid4eva on 2005-11-04
Hello, I am volunteering at a public school to teach Ubuntu to some students. I have installed Breezy Badger, but i can't get it to connect to the internet although I believe it to be on the school's network. I have a sign on, password, DNS server name, IP address of the computer, I believe the school has a firewall set up that may be preventing my access, can anyone offer some guidance,

Thanks.

---

### Post by dbott67 on 2005-11-04
It may be the firewall or some of the settings.

You would be best to speak with the network administrator to obtain the correct (and officially sanctioned) settings.

Many firewalls can block traffic based on **MAC address** (preventing an unauthorized/unknown computer from getting on the network), **IP address** (only allowing certain IP ranges to access certain resources), **Username**, etc.

If you just want to verify connectivity, try the following:
[LIST=1]
[*] ping various IP addresses of known, working local resources (such as the DNS server, gateway, printers, computers, etc.)   
[*]If you are able to ping those devices, you are "connected" to the network.   
[*]Next, try running a 'traceroute' to [www.google.com](www.google.com) or some known external IP address (btw, traceroute may need to be installed from Synaptic).  You can also use the graphical Network Tools under the Applications menu.   
[*]If traceroute provides results for google, then everything is working.  If not, make a note of where the trace stops (it would most likely be the gateway/router/firewall IP address). [/LIST] Please keep in mind that connecting an unauthorized computer to a network can be a serious offense in some places.  You could be suspended, expelled or even prosecuted for attempting to do this without proper authorization.

-Dave

---

