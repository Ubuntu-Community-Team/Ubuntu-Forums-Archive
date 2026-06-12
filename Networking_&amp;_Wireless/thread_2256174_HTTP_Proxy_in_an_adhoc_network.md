---
title: "HTTP Proxy in an adhoc network"
date: 2014-12-10
forum: Networking &amp; Wireless
---

### Post by dan148 on 2014-12-10
I'm trying to all my outgoing HTTP/S requests while connected to an adhoc network.  My setup looks like the following:
[LIST]
[*]Client A (no internet access) sends request for Server D
[*]A's outbound HTTP request gets rerouted to 127.0.0.1:7777 where an HTTP proxy is running
[*]The service on A:7777 forwards the request to B
[*]B forwards it to C
[*]C sends out the original HTTP request from A to D
[/LIST]
Now, while under a standard wireless network, I can set a HTTP/S proxy with no problem.  However when I change to an adhoc network I'm told that the hostname could not be resolved.  This lead me to research some more and realized that DNS queries are replaced with mDNS in adhoc networks.  With all that being said, my biggest issue is how to get all of A's outbound HTTP traffic to be proxied by it's service on 7777?  Do i need to write a custom script, or is there something out that that will currently do this for me?

---

