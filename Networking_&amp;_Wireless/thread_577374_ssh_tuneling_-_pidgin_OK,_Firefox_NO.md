---
title: "ssh tuneling - pidgin OK, Firefox NO"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by sexus6 on 2007-10-16
Hi
I connect to internet by a insecure lan that have configure smoothwall, a firewall with proxy capacities that log all web and instant messaging traffic.

I want to have secure web browsing and IM use. For this, I configure a external ssh server (at my home) that is prepared to make ssh tunels for two things:
1.- jumping blocking ports
2.- Don't let to logging my web browsing and IM .

For this, I use this command:

ssh  -N -l username -D 443 ip

where 

username = username of my external server at home
ip = ip of my external server at my home

After this, I configure pidgin, each account (msn, gtalk, etc) to use a socks4 proxy, with the server = localhost and port = 443. At this way, pidgin exit by 443 port, where he find a ssh tunel that connect directly to my home, in a ssh encripted way. None any kind of server (except ssh server) need for this at home server. And this works great!

I want to use the same tunnel to web browsing. I go to configure Preferences from firefox, and I configure the connection parameteres. I configure the proxy server, socks4, localhost, and port 443, the same like pidgin, but I can't browsing. There is no response at the firefox screen, none page is load.

Is needed to install any service in my home server like squid? If I have to install squid or something similar, why is the reason that pidgin can connect through the ssh tunnel withou any kind of service?

Can I use the same tunnel / port for the two apps (firefox and pidgin)?

What's the problem here?

---

