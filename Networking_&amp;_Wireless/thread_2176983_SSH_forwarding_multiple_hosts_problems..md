---
title: "SSH forwarding multiple hosts problems."
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by cromestant on 2013-09-26
Hello, 
I just realized that with PUTTY you can setup various tunnels using the same Local port
but when I try to do it on my ubuntu box I get the dreaded :
> bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 8080

I tried using :

```
ssh user@box -L 8080:remotehost1:8001 -L 8080:remotehost2:8001 
```

and it does not work, I'm sure if putty is able to do this then openssh can very well do it, I'm just not doing it right.

---

### Post by papibe on 2013-09-26
Hi cromestant.

Are you trying to create a tunnel using multiple hops?

Regards.

---

### Post by cromestant on 2013-09-26
no, it is single hop.
the issue is that I have various API servers to which I only have access from "box", and I 'd have to configure soap client to use more than one proxy which is a pain.
in essence testing on a windows box with putty I am able to create the FW on same local port for both ( even more) hosts.

Ideally a dynamic forward should work, but when I set it up, i can browse all of the "public" hosts, but not get to these hosts.

in essence these hosts ( host1 and host2) are only accessile from BOX, I 've tried setting the SOCKS proxy but it does not work.

---

### Post by cromestant on 2013-09-27
I have a screen shot from my windows box as to what I want to achieve with  my linux box:

[ATTACH=CONFIG]246541[/ATTACH]

as you can see I establish a few tunnels from the same port.

---

### Post by The Cog on 2013-09-27
That doesn't make sense to me. Which host should it forward the connection to? I bet you can configure as many as you like in the GUI but only one actually happens.

---

### Post by cromestant on 2013-09-27
I just checked, and you are right, the event log shows it created but only the first is connected, however they are used by the others too

How can I get dynamic forwarding to work for my internal DNS.

lets say my server is called sandbox, from sandbox I can connect and ping to apiserver1.domain.com and apiserver2.domain.com

if I create dynamic forwarding to that server, I can connect to facebook, google, etc but connecting to apiserver1.domain.com and apiserver2.domain.com does not work.

---

### Post by papibe on 2013-09-27
What kind of access do you need to the apiservers?

If you are going to accessing them using the browser, then you just may need to enable **'socks_remote_dns'** so that the DNS is resolved remotely on sandbox (read [this]("http://support.vpnsecure.me/articles/ssh-tunnelling-proxy-troubleshooting/ssh-socks-dns-leaks-in-mozilla-firefox")).

Regards.

---

### Post by The Cog on 2013-09-28
I really don't understand what you are trying to do, but why not listen on a different port for each final destination?

```
ssh user@box -L 8080:remotehost1:8001 -L 8081:remotehost2:8001
```

---

