---
title: "Privoxy + Tor no longer working"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by jgb2185 on 2007-08-26
I am suddenly unable to access any sites through the combination of Firefox 1.5.0.11 on Ubuntu 6.06 LTS (Dapper Drake), Privoxy 3.0.3, and Tor v0.1.0.16.

Privoxy is configured for use with Tor by adding the line 
```

forward-socks4a / 127.0.0.1:9050 .
```

to the top of the config file. The log indicates that Privoxy restarts OK:

```
Aug 26 17:18:14 Privoxy(b7d546c0) Info: Privoxy version 3.0.3
Aug 26 17:18:14 Privoxy(b7d546c0) Info: Program name: /usr/sbin/privoxy
Aug 26 17:18:14 Privoxy(b7d546c0) Info: Listening on port 8118 for local connections only
Aug 26 17:20:44 Privoxy(b7d546c0) Info: exiting by signal 15 .. bye
Aug 26 17:41:51 Privoxy(b7da76c0) Info: Privoxy version 3.0.3
Aug 26 17:41:51 Privoxy(b7da76c0) Info: Program name: /usr/sbin/privoxy
Aug 26 17:41:51 Privoxy(b7da76c0) Info: Listening on port 8118 for local connections only
```

The error thrown by Privoxy is:

```
404 This is Privoxy 3.0.3 on localhost (127.0.0.1), port 8118, enabled
No such domain
Your request for http://www.google.com/ could not be fulfilled, because the domain name www.google.com could not be resolved. 
```

I have removed both Privoxy and Tor using **apt-get --purge remove**, and then reinstalled. After adding the **forward-socks4a** into the Privoxy config file, this error remains.

I am uncertain how to proceed. How can I test Privoxy and Tor separately, to at least work out which one is at fault?

Thanks...

JGB

---

### Post by 686plus on 2007-08-29
I am having the same problem. I haven't used tor/privoxy in a while, so I'm not sure what has changed. Anyone have any thoughts?

---

### Post by 686plus on 2007-08-29
I checked my tor log file at /var/log/tor

```

Aug 28 ip.ip.ip.ip [warn] You are running Tor version 0.1.0.16, which will not work with this network.

```

I found this website and updated my version of tor, which fixed my problem:

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

---

### Post by Juan Largo on 2007-09-03
As of August 2007, tor version 0.1.0.x is no longer working.  You need to upgrade to a later version.  Visit the tor site to download it.

---

