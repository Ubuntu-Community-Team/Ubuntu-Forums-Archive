---
title: "Best VPN Ubuntu Server Client"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by kmccmk9 on 2013-12-20
Hello, so I have an established web server running under ubuntu server. I need to activate a vpn connection and route traffic when a specific url is requested. What is the best software that provides these options if any?

---

### Post by TheFu on 2013-12-20
I guess you've stumped us.

VPN servers generally run 24/7 on a known port. They are not started and stopped based on some website hit. "Best" is highly subjective - the **best** for many people is openvpn.  It has clients for almost all common platforms, it has options to be secure against NSA attacks, it can scale from 1 to 5000 users, and it has commercial support, if you need it.  With openvpn, the server controls routing, almost anything you can imagine can be accomplish, if you have the Linux skillz.

The downside is that openvpn is not trivial to setup and run.  Secure solutions generally have trade-offs.

There is always the ssh-tunnel method too.  If you run an ssh server, then your server-side setup is almost done.  Just user accounts and training is needed. To most end-users, ssh-based tunnels are harder than openvpn. OTOH, ssh has many more clients across many more platforms than openvpn.  The downside is that it uses TCP, so connections have much more overhead than openvpn.

I must be missing something basic in your requirements.  Do you want to run both the client AND the server or are you seeking a remote VPN exit node in a different country for "some reason?"

---

### Post by kmccmk9 on 2013-12-27
Hi thanks for the response. Basically I have the ubuntu server. It runs tomcat apache. Only under certain conditions do I want to rout the request to a different ip address.

---

### Post by TheFu on 2014-01-01
Perhaps you really want a **reverse proxy server**?  "nginx" can do this, as can "pound" and there is an apache module for this too.   The SSL termination will be on the reverse proxy, which can be exactly what you want ... or not.

I wrote this [http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers) a few yrs ago which may explain better.

If you really do want/need a VPN, please explain the routing needs in more detail.

---

