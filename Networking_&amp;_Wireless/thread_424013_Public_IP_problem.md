---
title: "Public IP problem"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by danut on 2007-04-26
I have a public IP and i would like to use it both outside and inside my network.
in fact it works both inside and outside but only with HTTP.
I installed and configured apache with HTTPS, but it only works outside.

then:
outside the network http and https work fine with public IP
inside the network http and https work fine with LOCALHOST
inside the network http works fine and https doesn't work

could somebody help me?

---

### Post by .rdg on 2007-04-26
It's difficult to get what is your network build like, but it's definitely working - your public IP is visible in the net and the private IP as well. Apache listens on port 80 on both of these IPs, but it's not listening on both for https requests - just on the public IP. That's what I read in your post.

So please do the following in the terminal:

netstat -lnt | grep -e ":80" -e -e ":443"

That command should show you on what IPs your PC is listening on port 80 (http) and 443 (https). It should show 2 lines (or 3 - including 127.0.0.1 = localhost) with :80 and only 1 with :443 (https), showing only your public IP. If so - please set up apache to listen for the local one as well in /etc/httpd/conf.d/ssl.conf (or something similar - don't have any http server at hand to look ATM).

---

### Post by danut on 2007-04-27
netstat -lnt | grep -e ":80" -e ":443"

tcp6 0 0 :::80 :::* LISTEN
tcp6 0 0 :::443 :::* LISTEN

---

### Post by .rdg on 2007-04-27
Seems you only listen on all IPv6 addressess for both http and https requests - but no IPv4. Could you be more specific as to your network build? Perhaps then I could give a better answer.

---

### Post by danut on 2007-04-27
i'm not an expert of networking :(
anyway, between the computer with Apache and internet there's a router
and i have this static IP forwarded to a local IP with all ports opened..

i configured apache with htpps and everything works fine BUT i can't use the static IP with https inside my network.. i would expect both don't work.. but http work with static IP!!!

---

### Post by .rdg on 2007-05-06
Sorry for the delay - been away for few days.

I still don't have the clear picture of what you are actually doing - so I'll assume some situation and perhaps it's what you're doing.

Your public IP is 1.2.3.4 and it's bound to [www.example.com](www.example.com). Your router forwards all traffic on ports 80 (http) and 443 (https) to your local PC with apache (ip 192.168.0.2; router has also 192.168.0.1). All of these are just for example off course.

You're trying if your https works from outside your network - and it works fine (router forwards all traffic to local PC). If you do the same - it doesn't. All is fine with http, no matter from where you are testing. In both test you try to connect to [www.example.com](www.example.com) (IP 1.2.3.4) - this one is really important.

If the above assumptions are correct you probably have a problem with port forwarding from inside your network to your local PC - or actually the problem is with the https requests (using ssl). If so - I would advise you to connect from inside your LAN to the LAN IP you use on PC with apache. It would not require any routing and port-forwarding back to LAN. The only problem with it is that you would have to set up a local domain (example.lan for example :D), but that would also require to set up your apache-PC with additional IP address (subinterface) and listen on it for https requests as well. I won't give any more info now because the assumptions might be wrong - and it would be pointless then.

Hope this somehow clears things up a bit. Regards,
.rdg

---

