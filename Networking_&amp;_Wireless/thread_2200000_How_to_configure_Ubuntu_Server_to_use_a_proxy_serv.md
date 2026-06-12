---
title: "How to configure Ubuntu Server to use a proxy server"
date: 2014-01-17
forum: Networking &amp; Wireless
---

### Post by pravsemilo on 2014-01-17
I have 2 instances (Proxy_Server & Web_User) hosted on  EC2, both running Ubuntu Server 12.04. On one of the instances  (Proxy_Server) I have Squid installed. I want to use Proxy_Server as a  proxy for the other instance (Web_User).
  Under normal circumstances in EC2, Web_User would be using a  transparent proxy which would redirect the requests to websites on the  internet. What I want is to route those requests via the Proxy_Server  through Squid. Additionally I want this to happen for all TCP  connections.
  
[LIST=1]
[*]I have tried configuring http_proxy and HTTP_PROXY in  etc/environment. But that would be for only HTTP requests. So a wget  will work fine but a normal socket connection to the same website  wouldn't.

[*]I have also tried port forwarding and tunneling to have a SOCKS  proxy running on Web_User tunneling to Squid on Proxy_Server. But this  brings back me to point 1. How do I make Web_User to be aware of  Proxy_Server? I can make firefox in Web_User to be aware of Proxy_Server  but how do I do that same system wide?
[/LIST]

---

