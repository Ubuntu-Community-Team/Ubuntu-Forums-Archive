---
title: "Tor error messages"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-15
Recently i started using Tor, everything was fine for a while, but now i get these error messages after a few minutes:

```
jamie@jamie-kubuntu:~$ tor
Apr 15 21:23:10.963 [notice] Tor v0.2.1.25. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Apr 15 21:23:11.078 [notice] Configuration file "/usr/local/etc/tor/torrc" not present, using reasonable defaults.
Apr 15 21:23:11.078 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Apr 15 21:23:11.097 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 15 21:23:11.157 [notice] Parsing GEOIP file.
Apr 15 21:23:11.405 [notice] OpenSSL OpenSSL 0.9.8g 19 Oct 2007 [90807f] looks like it's older than 0.9.8l, but some vendors have backported 0.9.8l's renegotiation code to earlier versions.  I'll set SSL3_FLAGS just to be safe.
Apr 15 21:23:12.228 [notice] We now have enough directory information to build circuits.
Apr 15 21:23:12.228 [notice] Bootstrapped 80%: Connecting to the Tor network.
Apr 15 21:23:13.297 [notice] Bootstrapped 85%: Finishing handshake with first hop.
Apr 15 21:23:17.283 [notice] Bootstrapped 90%: Establishing a Tor circuit.
Apr 15 21:23:20.218 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Apr 15 21:23:20.218 [notice] Bootstrapped 100%: Done.
Apr 15 21:28:02.154 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'PrivacyNow'. Retrying on a new circuit.
Apr 15 21:28:02.154 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'PrivacyNow'. Retrying on a new circuit.
Apr 15 21:28:05.167 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'PrivacyNow'. Retrying on a new circuit.
Apr 15 21:28:15.234 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit '703server'. Retrying on a new circuit.
Apr 15 21:28:17.249 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit '703server'. Retrying on a new circuit.
Apr 15 21:28:17.249 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit '703server'. Retrying on a new circuit.
Apr 15 21:28:20.270 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit '703server'. Retrying on a new circuit.
Apr 15 21:28:35.367 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'Shitblaster'. Retrying on a new circuit.
Apr 15 21:33:32.760 [notice] Have tried resolving or connecting to address '[scrubbed]' at 3 different places. Giving up.
Apr 15 21:35:01.990 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'peterhusten'. Retrying on a new circuit.
Apr 15 21:35:01.990 [notice] We tried for 15 seconds to connect to '[scrubbed]' using exit 'peterhusten'. Retrying on a new circuit.

```

Sometimes i get error messages looking like this: 
```
Apr 15 21:43:44.213 [notice] Tried for 120 seconds to get a connection to [scrubbed]:0. Giving up. (waiting for socks info)
Apr 15 21:45:01.706 [notice] Tried for 120 seconds to get a connection to [scrubbed]:0. Giving up. (waiting for socks info)
```

```
Apr 15 21:49:20.163 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
Apr 15 21:49:30.233 [notice] Tried for 120 seconds to get a connection to [scrubbed]:80. Giving up. (waiting for circuit)
Apr 15 21:52:21.820 [notice] Have tried resolving or connecting to address '[scrubbed]' at 3 different places. Giving up.
Apr 15 21:53:43.765 [notice] Tried for 120 seconds to get a connection to [scrubbed]:0. Giving up. (waiting for socks info)

```

When i use the terminal i can connect to Tor for a while, however when i use Vidalia (the gui) it gets stuck on 'connecting to a relay directory (no route to host)

---

### Post by phidia on 2010-04-15
I don't know but I think the tor mailing list [resources]("http://www.torproject.org/documentation.html.en") will provide more specific and usable help for you. And see these [archives]("http://archives.seul.org/tor/relays/") from the above linked site.

---

