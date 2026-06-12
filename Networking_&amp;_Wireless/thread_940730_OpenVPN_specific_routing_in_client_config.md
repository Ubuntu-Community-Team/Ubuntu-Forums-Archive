---
title: "OpenVPN: specific routing in client config"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by hsmfos on 2008-10-07
I use OpenVPN to connect to a work server, but not using it as a default 
gateway. From what I understand of it, the server tells my client when 
to use the vpn-connection, i.e. when accessing specific sites/servers 
(intranet, ftp, ssh, etc). 

But what happens when the server says: ok, from now on you (the 
client) should also route google.com, yourbank.com, paypal.com, etc. 
through my OpenVPN server? I suppose it'll use the vpn connection 
instead of my own internet connection? I'm pretty sure this won't 
happen, but it just feels wrong... 

So, my question: is there a way to prevent this? E.g. by adding only 
specific ips to the client configuration, so that no matter what the 
server says, I can be sure that my client only uses the vpn connection 
for the connections that I specified? 

Thanks in advance!

---

### Post by kevdog on 2008-10-13
Im not sure what you mean -- however to route my requests through the vpn gateway, all I did in the client config file was to put this line for example:

redirect-gateway def1

---

