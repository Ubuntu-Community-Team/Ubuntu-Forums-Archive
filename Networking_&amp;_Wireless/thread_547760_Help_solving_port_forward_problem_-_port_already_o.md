---
title: "Help solving port forward problem - port already open?"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by reader4 on 2007-09-10
This used to work, but doesn't anymore and I cannot for the life of me figure out what changed.  I try to forward a port but get (abbreviated output):
```
$ sudo ssh -vL 22:target_server:22 me@intermediate_server
debug1: Authentication succeeded (password).
debug1: Local connections to LOCALHOST:22 forwarded to remote address target_server:22
debug1: Local forwarding listening on 127.0.0.1 port 22.
bind: Address already in use
socket: Address family not supported by protocol
channel_setup_fwd_listener: cannot listen to port: 22
Could not request local forwarding.
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8

```

So, it seems something else is already using port 22, which seems to be confirmed:
```
$ nmap 127.0.0.1

PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp
```

But I can't figure out what.  I haven't been able to find out the answer by searching so am looking for help to troubleshoot this problem.

---

### Post by noob12 on 2007-09-10
Port 22 is the port generally used by the ssh server itself.  So you can't tunnel that.

---

### Post by reader4 on 2007-09-13
I can use a different port on my local machine (eg, 127.0.0.1:3000) but it is slightly more cumbersome, since programs default to port 22 for sftp.  The part I was more interested in is why it used to work just fine to forward port 22, but now it is an issue.

---

