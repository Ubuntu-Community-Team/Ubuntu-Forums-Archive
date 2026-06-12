---
title: "Reverse SSH problems: &quot;failure forwarded-tcpip&quot;"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2016-04-26
Hey guys,

I am trying to reverse SSH from my linux machine to my home machine:

```
/usr/bin/ssh -N -R 1111:127.0.0.1:22 xxx@yyyyy.no-ip.info
```

Everything setup well and good. 

```
Authenticated to xxx ([yyyyy]:22).
debug1: Remote connections from LOCALHOST:1111 forwarded to local address 127.0.0.1:22
debug1: Entering interactive session.
debug1: remote forward success for: listen 1111, connect 127.0.0.1:22
debug1: All remote forwarding requests processed

```

But when I am trying to SSH back to my linux machine I get the error:

```

ssh whatever@localhost -p 1111 
ssh_exchange_identification: read: Connection reset by peer
```

On the terminal which I've setup the reverse SSH connection, with verbose mode I get:
```

debug1: client_input_channel_open: ctype forwarded-tcpip rchan 1 win 262144 max 65536
debug1: client_request_forwarded_tcpip: listen 127.0.0.1 port 1111, originator 127.0.0.1 port 55182
WARNING: Server requests forwarding for unknown listen_port 1111
debug1: failure forwarded-tcpip
```

Is this a bug or am I doing something wrong?

There is another machine currently also  reverse SSHing to my server but I use a different port for that one (2222)

```
/usr/bin/ssh -N -R 2222:127.0.0.1:22 xxx@yyyyy.no-ip.info
```

What am I missing?

---

### Post by djgenesis on 2016-05-04
Anyone??

---

