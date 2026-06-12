---
title: "Forward traffic"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by midna on 2007-02-07
I'm looking for a way to forward all information to my router, except for certain things (namely p2p, ssh, ftp, and http) and make the router believe it is still connected straight to the internet.

Heres the setup and the reason why I want to do this. I have a company router that the IT department has installed at my house on my cable internet line that provides a secure VPN connection to one of the computers at my home to the company. For all the other computers it provides a regular connection. However, UPnP is not enabled on the router, port forwarding is not set up, and worst of all the IT has me locked out of the router and will charge me per change they make to its configuration. It's a firebox so I'm SOL when it comes to cracking the stupid thing, and I don't want to do a hard reset because I might lose key settings information.
I also have a DSL connection which I have been using for everything I want, except that it is way slower than the cable connection.

My idea: Connect an ubuntu server straight to the cable modem and pass everything to the router as if the server wasn't there except for the key services I wish to access (torrents, ssh, ftp, and http).

Is my idea possible and how would I go about doing so? Links to related information do wonders as I am not opposed to learning on my own, I just have no idea where to start. :)

---

