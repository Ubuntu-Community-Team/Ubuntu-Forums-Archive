---
title: "Can't resolve MX records for outbound emails"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by dehuszar on 2008-06-06
I'm reeling from AT&T's reconfiguration of their mail-relay policies.  We have a Domino server running on Ubuntu Hardy, and we are now forced to send directly out to the internet.

If possible, I'd prefer to not have to set up BIND.  We have a DynDNS account set up as well.  Our INBOUND MX records are working fine, but any attempt to send OUT gives me a "no route known to the destination address" error.  IBM has walked me through the configuration docs and it appears to be an Ubuntu issue.

Doing an nslookup on gmail.com with type=mx gives me the same "no route to host" error.  I have no iptables policies, nor ufw configurations.

Does anyone have any ideas of what I can do to make this work?

Thanks in advance,
Sam

---

### Post by dehuszar on 2008-06-11
Okay, so I've tried a few other things.  First off, my attempts to do this from my home server (as opposed to my client's) works fine.  I can telnet to mail servers on port 25 successfully with the following:

```
telnet gmail-smtp-in.l.google.com 25
```

Executing the same command on my client's network gives me an "unable to connect to remote host: No route to host error after trying to resolve the hostname (which it does successfully, incidentally; the ip address which my server connects on, cannot connect from my client's server/network).

My home machine uses Comcast, the client's connection is provided by AT&T.  I don't know if that's an issue, but otherwise the configurations are nearly identical.  They both use Ubuntu 8.04, they both are running Domino 8+.  The only thing I can think of is that I'm missing a package that would otherwise do this work, or something is misconfigured.  Neither has a DNS server like Bind or DaemonTools, so those aren't needed to work.

Anyone have any idea on what I can check?

---

