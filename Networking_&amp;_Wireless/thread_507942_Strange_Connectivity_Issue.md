---
title: "Strange Connectivity Issue"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by tself on 2007-07-23
Hi,

I'm running 6.06 server, and have just recently started to experience a strange connectivity issue. 

The server is connected to a cisco switch, has internet access via a layer 3 cisco switch to a cisco asa firewall and a leased line connection to the internet.

The problem i am having is the server intermittently loses connectivity to anything off network. I.e. it is still accessible to and from anything on its local subnet i.e. 192.168.1.0 but trying to connect to it from off network, or it trying to ping to something off network doesn't work. A reboot appears to fix it (sometimes), but this needs to be done 3 - 4 times a day which is now a very big problem.

All cables have been replaced ports on switch changed, the network switches are working correctly as this is not affecting any other equipment other than the Ubuntu 6.06 servers, the server hardware is not to blame as i've tried building the system on various hardware and am still getting the same problem.

I believe the problem is caused by icmp redirects, as the server connects to the gateway 192.168.1.1 but is then redirected to 192.168.1.254, this isnt a problem for any other machines on the network other than the Ubuntu servers.

Icmp redirect does appear to work for a short while as it allows off network communication then all of sudden the connectivty off network will be lost, and the machine needs to be rebooted. Is there a bug? Why does it suddenly ignore the icmp redirects?

Strangely the box has been running fine for the last year using icmp redirects, then 3 weeks ago, the router on a stick that was performing the redirection was replaced with a layer 3 switch. But i can't understand why this would affect anything as all other equipment works quite happily with these redirects.

Anyone have any ideas? i'm about to scrap Ubuntu and find a different distro as i can't seem to find out what is happening here.

Thanks in advance for any help you might have.

---

