---
title: "Redirecting internal ports through a SSH tunnel"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by viperuws on 2007-01-14
OK, to start, I am somewhat new to linux in general but considering this is a bit more of an in depth question then "how do I make my wireless work" I figured I would post it here. I am running Ubuntu 6.10 and know some basic stuff.

I am looking to redirect all internal ports to a single port (22 for SSH) and send it to a remote pc over a SSH tunnel.

I looked around and I was wondering if this would work?

ssh -L *:remotepc.com:* [email]username@remotepc.com[/email]

I am guessing this would cause *(all local ports) to travel to remotepc.com(my remote SSH server) to *(ports on my SSH server). but it doesn't want to let me use the wild card *.

An alternative would be to use another way to redirect all internal ports to another port and put that port number through the tunnel.

Any help with this problem would be great.

Oh and the more I use Linux, the more I am loving it over Windows. :-D

---

### Post by souki on 2007-01-14
this cannot work, because you have to be sure the ports are not used on localhost

if you want a permanent tunneled connexion you need a VPN, this is not easy to set up
if you want occasional port tunneling, you can stay with ssh and simplify your command line by using the file ~/.ssh/config

here is an example from my  ~/.ssh/config
the bonus is that you can also tunnel host behind the firewall

[html]Host example_tunnel
        IdentityFile ~/.ssh/id_rsa
        HostName myhost.mydomain
        Port 2222
        User myuser
        Compression no
        Protocol 2
        LocalForward 8080 127.0.0.1:8080
        LocalForward 9080 192.168.1.151:80
        LocalForward 10080 192.168.1.151:8080
        LocalForward 10082 192.168.1.151:8082
        LocalForward 8070 192.168.1.100:5070[/html]

---

### Post by viperuws on 2007-01-14
What about hosting a proxy server on my laptop with socks5 and then just forwarding that port over SSH.

I am really trying to play WoW over a firewalled network at my school.  :mrgreen: I managed to get it working with windows using a tunnel with putty and using freecap to encapsulate all traffic from wow.exe to a single port and sending that through the tunnel.

So is there some kind of program or command to encapsulate traffic from a program or even my laptop to a single port?

---

