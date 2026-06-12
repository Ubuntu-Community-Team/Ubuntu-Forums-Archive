---
title: "Tunneling HTTP over SOCKS?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by JuhazOne on 2008-05-09
The short question: how do I tunnel HTTP requests through a SOCKS proxy?

I've learned, though, that when asking for help, you shoud tell what you're trying to achieve, not ask about a specific way of doing it. So here comes the long question...

I'm a student at two universities, Helsinki University of Technology (HUT) and University of Helsinki (UH). In both universities I have some stuff that can only be accessed from within the university's own network. I can SSH to either uni or use OpenVPN with UH. Both universities have a HTTP proxy that I can use, and so far I've used those. There's an annoyance with the UH proxy, though, since it asks for one-time username and password if I haven't used the connection for a while (a couple of hours I think). This isn't very convenient so I'd like to skip using this www proxy.

I've experimented with OpenVPN to route connections directly through the VPN server. The problem is that if I need to add another host to route I need to edit /etc/openvpn/openvpn.conf every time. Proxy auto-config is much more flexible in that I can use regex matching on the URL if I want to, for example.

I recently learned that SSH has a built-in SOCKS server. I immediately thought that it could help me to avoid the HTTP proxy at UH. And it can... But I use mostly Opera, and Opera doesn't support SOCKS. Firefox works fine through SSH and SOCKS, but I'd rather use Opera if I can. I've spent a few hours now trying to find a program that acts as a HTTP proxy and tunnels requests through a SOCKS proxy.

So far I've tried tinyproxy, but for some reason it returns Opera an error page. There's a line in the config file that reads "upstream localhost:8801", and 8801 is the SSH port with SOCKS. I thought first that tinyproxy isn't compiled with SOCKS support, but compiling it myself didn't help. The log files didn't tell that there's anything wrong and there's practically no documentation available, so I gave up on tinyproxy. I tried privoxy next, but it too told me that the page can't be accessed and the logs weren't of any help, so I gave up again.

I've also taken a look at tsocks to see if I could use it to force Opera to tunnel requests through a SOCKS proxy. It seems to me that it can... if I tunnel ALL requests. That wouldn't work since I need to be able to tunnel through at least two SSH connections.

So far it looks to me that a HTTP proxy with SOCKS support would be the best solution... However, the programs I already tried didn't seem to work. Any ideas on what to try next?

---

### Post by kevdog on 2008-05-09
Only used firefox in combination with ssh proxy. Dont know anything about Opera.

---

