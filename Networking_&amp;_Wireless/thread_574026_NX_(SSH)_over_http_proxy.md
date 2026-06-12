---
title: "NX (SSH) over http proxy"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by HAARP on 2007-10-12
Hi there.

I recently discovered NX. It's kinda like VNC, but better. I'm not using freeNX, but the nomachine.com one (Free Edition 3.0.0-74), since it actually works. NX is based on SSH but provides a graphical interface to your machine.
I try to access my machine at home from work.
But there's a problem. Here's some information first:

connection:@ work over proxy, @ home directly to internet with dynamic IP and DynDNS
proxy: only HTTP traffic allowed, authentication required. Browsers on Windoze/Linux work when set up correctly.
OS: @ work Windows, @ home Edgy

Direct connections from different locations to my NX server at home work. But at work, I'm getting problems with their proxy.

1st try:
I set the NX client (the Windows one) up to use the proxy and authentication.
results: didn't work
conclusion: proxy only lets http traffic through

2nd try:
Use desproxy to tunnel through proxy
results: proxy returns "not allowed"
conclusion: desproxy does not imitate http traffic close enough

3rd try:
Use httptunnel (which needs to be set up both on client and server)
configuration (port): NX client -> (900) -> httptunnel@work -> (80) -> proxy@work-> (80) -> httptunnel@home -> (22) -> NX server
results: connection to PC at home works, however aborts at some point.
test: Tried the same client configuration (but without proxy) at a friends
results: same as at work
test2: Tried the same client configuration (but without proxy) at home in local network
results: It works.
conclusion: wtf?

I get a connection alright, but it aborts. 

client log:
```
NX> 203 NXSSH running with pid: 5532
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 900
ssh_exchange_identification: Connection closed by remote host
```

I can't figure out why this happens. There's nothing in the logs on my machine (server)
Obviously, the remote host (which is my machine) closes the connection. Why does it do that? I wonder if that's because it discovers that a tunnel is used.

Any ideas?

---

### Post by Jimmey on 2007-12-10
I'll need to do a bit more research about your situation before I can help you out a little more, but, I'll advise that you can use SSH for an X session. 

Look at some of these pages for more information on SSH.

Sorry I can't be more help at the moment, I'll get back to you on this one.

---

### Post by kevdog on 2007-12-10
You need to be able to ssh first over port 80.  All this testing can be done at the command line.  Can you do this first?

---

### Post by ayenack on 2007-12-10
You may need to turn off intrusion detection on your router.

---

