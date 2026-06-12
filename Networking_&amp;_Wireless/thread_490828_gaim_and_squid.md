---
title: "gaim and squid"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by savimonty on 2007-07-02
Hi,

I tried connecting gaim via a squid proxy server whose ports for yahoo and jabber are opened ..

-- ---- snipet squid.conf ---- ----- i just added these 2 lines ---

acl Safe_ports port 1396        # YAHOO/GAIM
acl SSL_ports port 5222         # GTalk/GAIM

---------------- end of snippet ----

--- access.log file... ------------


1183430542.972      0 192.168.1.11 TCP_DENIED/403 1396 CONNECT scs.msg.yahoo.com:5050 - NONE/- text/html

1183430743.693    616 192.168.1.11 TCP_MISS/200 369 CONNECT talk.google.com:5222 - DIRECT/72.14.253.125 -

-------------------------------------------------
gtalk/gaim gives me a "SSL Handshake failed error"

is there anything else i have to do either in the squid.conf file or in the gaim settings?

Thanks a lot in advance,

Savio Monteiro

---

