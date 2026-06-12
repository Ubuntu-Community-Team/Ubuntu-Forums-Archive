---
title: "openvpn does not apply configuration options"
date: 2017-08-03
forum: Networking &amp; Wireless
---

### Post by jamapii on 2017-08-03
Title should be: openvpn does not apply config options

Hi,

the new openvpn 2.3.2 in ubuntu 14.04.5 LTS is completely broken. It does not (well, selectively) use its config file, as can be seen from "WARNING...inconsistent..." lines in the logs, it always, no matter how anything is configured, show "Bad decompression header" lines on both sides, it provokes FRAG_IN, FRAG_WHOLE and similar lines in the server but not the local logs, no matter the configuration (which is not used anyway).

The config file ignoring is selective, random but constant. I can add options and this has an effect, I can change options that matter and they are ignored. The crazy values on some options are random but (almost) constant too. If they change, they change by themselves. e.g. link-mtu from 1558 to 1557.

The breakage started 2017-06-17 according to server logs, but the local log says the openvpn is compiled on 2017-06-22 (I dont have old logs here). So there must have been 2 consecutive updates, both broken.

What is different in this new update, can it be configured to work at all? How can I revert to an older version?

---

### Post by jamapii on 2017-08-04
Even with old openvpn version, the configuration is no longer applied.

I also tried to recreate the lines (for possible non-working stealth space characters), run through dostounix, and made world-readable. It does not help.

Is there a way to debug it to find what configuration is applied, and why, and why not?

---

### Post by jamapii on 2017-08-04
OK, so these options MUST be in <connection> sections, if any such sections exist. Outside of connection sections, they go into a "default" and are not applied.

With this change, it works. Also it is necessary to change /etc/logrotate.d/rsyslog to keep logs for some reasonable time.

---

