---
title: "Assign subdomain name to a server"
date: 2015-07-19
forum: Networking &amp; Wireless
---

### Post by dmytro2 on 2015-07-19
Hello everyone) I know that this question might be a little off topic but I could really use some help. The problem is as follows: I need to configure my local network so that a particular machine (ip address) is accessed by a specified domain name.
My WAN IP (router external ip) is linked to domain name, say **router.ddns.net**, and forwards certain ports to server machine. What I want is to somehow configure my local network so that a server machine can be accessed as **machine**.**router.ddns.net** from outside of my LAN. How can I do that? Thanks)

Server machine has Ubuntu Server 15.04 installed.

---

### Post by TheFu on 2015-07-19
> **dmytro2 said:**
> Hello everyone) I know that this question might be a little off topic but I could really use some help. The problem is as follows: I need to configure my local network so that a particular machine (ip address) is accessed by a specified domain name.
My WAN IP (router external ip) is linked to domain name, say **router.ddns.net**, and forwards certain ports to server machine. What I want is to somehow configure my local network so that a server machine can be accessed as **machine**.**router.ddns.net** from outside of my LAN. How can I do that? Thanks)

Server machine has Ubuntu Server 15.04 installed.

So I was looking to see if you'd asked any ssh/sftp questions and saw this one.
How the outside world sees your internal network is control by the outside world, normally through DNS. While you can run your own DNS, it is one of the most hacked services running on the internet. Back in 2002, my DNS server was hacked.  I'd been running it "without problems" for about 5 yrs, so just because someone says it is easy (which is true), doing it in a secure way is hard.  Pay someone else to do that so you can sleep at night and on weekends.

So - if you have a DNS provider, just add another record that points to your WAN IP under a different name.  Then use the port to determine which internal server IP that port forwards at.  If you need to run multiple services or virtual web servers on port 80, then you can use a reverse proxy to split the traffic by which DNS name the requester asked for and forward to the appropriate back-end system(s).  This is one method for simple web site scaling.  With nginx as the reverse proxy, look at the upstream stanza and proxy_pass and location @hostname settings for "server". There are a few other reverse proxy tools - pound, ha-proxy, and apache has one, of course.

The short answer is, if you don't handle the forwarding by using unique ports for each service, then you have to use a reverse-proxy.  Reverse proxies don't work for every service.  You can use one for an SSL terminator for HTTPS or plain HTTP traffic which is handy. More complex protocols may or may not work.

Anyway - hope this helps.

---

### Post by dmytro2 on 2015-07-19
Thanks for your reply) It was helpful, so I think I will stick to forwarding for now. Thanks again)

---

### Post by TheFu on 2015-07-19
A few links that might help with more concrete details.

[http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers) might clarify.
and 
[http://blog.jdpfu.com/2011/07/03/Large-Blog-Website-Republishing-Our-Articles](http://blog.jdpfu.com/2011/07/03/Large-Blog-Website-Republishing-Our-Articles) - some load balancing.

---

