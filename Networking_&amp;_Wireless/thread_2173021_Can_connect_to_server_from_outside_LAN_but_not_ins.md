---
title: "Can connect to server from outside LAN but not inside LAN"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by l0uismustdie on 2013-09-07
I am running Ubuntu 12.04 on an older generation Macbook Pro (no version of OS X left on the laptop, only Ubuntu). This is connected to a Medialink wapr300n router. This machine is set to a static IP and ports have been forwarded to it for ssh and http. In addition I have a domain name registered with dyndns.org which has been turned on in the router preferences. All of this is confirmed to be functional (the domain name has been updated and tied to my IP, the ports are open and being forwarded to this machine). The problem I am facing is that I cannot access the domain name from my local network. For example a command such as:

```

ssh -v user@my-domainname.com

```
when issued from my local network will result in:
```

OpenSSH_5.9p1, OpenSSL 0.9.8x 10 May 2012
debug1: Reading configuration data /Users/****/.ssh/config
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: /etc/ssh_config line 53: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to my-domainname.com [*.*.*.*] port 22.
debug1: connect to address *.*.*.* port 22: Connection refused
ssh: connect to host my-domainname port 22: Connection refused

```
However, this same command issued from a remote location will be successful. If anyone has any ideas about this I would be greatly appreciative. It feels like an issue with the router, but I've scoured the preferences and am not finding much.

---

### Post by John_Petrucci on 2013-09-07
Does the [FONT=courier new]my-domainname.com [/FONT]resolve to the same (public) IP internally?  Can you ping to the hostname?  Might need to set up "NAT reflection" on the router. - [http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback](http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback)

---

### Post by l0uismustdie on 2013-09-07
John, good shout, and interesting article. It lead my down a road to turn on DMZ for that machine and things seem to be working now. cheers.

---

