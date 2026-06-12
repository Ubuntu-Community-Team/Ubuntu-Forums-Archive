---
title: "Strange Connection"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Randy R on 2007-02-20
When I do lsof -i a connection is shown:

[INDENT]freshclam  6165       clamav    0u  IPv4  64194       TCP 208-000-00-160.randy.trial.net:50388->kagami.redwire.net:www (ESTABLISHED)[/INDENT]

Note: ip address changed for obvious reasons

I know that kagami.redwire.net is the mirror site for apache. Does anyone know what this connection may be? I have never purposely setup a mirror for apache.

---

### Post by renzokuken on 2007-02-20
well frshclam and clamav are antivirus, may be it is something to do with auto-updates

---

