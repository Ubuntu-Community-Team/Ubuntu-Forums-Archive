---
title: "SSH port forwarding"
date: 2020-07-14
forum: Networking &amp; Wireless
---

### Post by gebseng on 2020-07-14
Hi everyone,

To get remote access to my home server (running Ubuntu Server 20), I forwarded port 22 to port 3xxxx in my rounter.

In [COLOR=#4D5156][FONT=arial]/etc/[/FONT][/COLOR][COLOR=#5F6368][FONT=arial]**ssh**[/FONT][/COLOR][COLOR=#4D5156][FONT=arial]/sshd_config, I inserted:

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Menlo]AllowTcpForwarding remote[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GatewayPorts yes
```

But I still get a "Operation timed out" when I try to log in via 

```
ssh user@[external ip] -p 3xxxx

```
I am able to ping [external ip] -p 3xxxx

What is missing?

thanks, geb[/FONT][/COLOR]

---

### Post by TheFu on 2020-07-14
Try:
```
PORT=3xxxx
ssh -f -C -D $PORT  [external ip] -NT &
```

BTW, settings for this stuff are easier added to the ~/.ssh/config file on the client so you never need worry about IP, port, userids from the client. Every ssh-based tool honors the ~/.ssh/config file settings.

```
host srv1804
  user thefu
  hostname 172.22.22.221
  port 22
host ex-srv1804
  user thefu
  hostname 50.22.22.221
  port 63022
```

so ...
```
ssh -f -C -D $PORT  ex-srv1804 -NT & 
```
Then connect to localhost:3xxxx to be dropped onto srv1804 for LAN access.  If you tell a browser that localhost:3xxxx is a SOCKS proxy, you'll have access to LAN-only webservers.

---

### Post by gebseng on 2020-07-15
Thanks for the reply!

When I try

```
PORT=3xxxx
ssh -f -C -D $PORT  [external ip] -NT &

```

I get the response:

```
[COLOR=#000000][FONT=Menlo]ssh: connect to host [xxx.xxx.xxx.xxx] port 22: Connection refused[/FONT][/COLOR]
```

I'm not sure why it tries port 22 instead of the port specified in the first line

---

### Post by TheFu on 2020-07-15
Did you setup the ~/.ssh/config as specified for your system?

The PORT= is for the localhost port which gets tunneled through the ssh connection. It has nothing to do with the actual ssh connection port.

---

