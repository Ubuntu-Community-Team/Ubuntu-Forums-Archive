---
title: "Vidalia not working"
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by Vombocorn on 2014-07-26
Hello,

I installed Vidalia from Ubuntu Software Store, when I try to connect to the Tor network, it comes up with that.

[PHP]Jul 26 15:01:38.736 [Notice] Tor v0.2.4.20 (git-0d50b03673670de6) running on Linux with Libevent 2.0.21-stable and OpenSSL 1.0.1f.
Jul 26 15:01:38.736 [Notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
Jul 26 15:01:38.736 [Notice] Read configuration file "/home/vombocorn/.vidalia/torrc".
Jul 26 15:01:38.736 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 26 15:01:38.736 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jul 26 15:01:38.736 [Warning] /var/run/tor is not owned by this user (vombocorn, 1000) but by debian-tor (116). Perhaps you are running Tor as the wrong user?
Jul 26 15:01:38.736 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can connect to it, so Tor is being careful.)
Jul 26 15:01:38.736 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jul 26 15:01:38.736 [Error] Reading config failed--see warnings above.[/PHP]

People have sujested that Vidalia is out-dated. Ihave tried finding the latest version online but can either find a file called "start-tor-browser" that comes up with a text editor and can't execute it, or I find TorBrowser, the browser not the Vidalia version.

Can someone help me please!
Thank you!

---

### Post by Vombocorn on 2014-07-26
I am trying to run Vidalia on Ubuntu 14.04. When I launch it it comes up with

 [ATTACH=CONFIG]255042[/ATTACH]

I click on the log and it says that /var/run/tor doesn't exit (which it **DOESN'T**).

Here is the full error log
```
Jul 26 20:04:13.446 [Notice] Tor v0.2.4.20 (git-0d50b03673670de6) running on Linux with Libevent 2.0.21-stable and OpenSSL 1.0.1f.
Jul 26 20:04:13.446 [Notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
Jul 26 20:04:13.446 [Notice] Read configuration file "/home/vombocorn/.vidalia/torrc".
Jul 26 20:04:13.449 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 26 20:04:13.449 [Warning] Directory /var/run/tor does not exist.
Jul 26 20:04:13.449 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can connect to it, so Tor is being careful.)
Jul 26 20:04:13.449 [Notice] Closing partially-constructed Socks listener on 127.0.0.1:9050
Jul 26 20:04:13.449 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jul 26 20:04:13.449 [Error] Reading config failed--see warnings above.
```

Can someone help me fix this please!
Thank you!

---

### Post by bapoumba on 2014-07-26
Threads merged.

---

