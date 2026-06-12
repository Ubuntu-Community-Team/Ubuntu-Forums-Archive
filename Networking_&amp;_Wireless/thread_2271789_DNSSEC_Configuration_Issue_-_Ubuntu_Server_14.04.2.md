---
title: "DNSSEC Configuration Issue - Ubuntu Server 14.04.2"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by lektronx2 on 2015-04-01
I'm currently receiving the following errors from my bind server, which is configured to automatically update dnssec zones every hour: [http://deviance.us/dnssec_errors.txt](http://deviance.us/dnssec_errors.txt). Other than these errors, I can find no other problems with configuration - xternal tests (dig, whois, etc) seem to indicate that DNSSEC is otherwise properly configured and functioning.

I had to re-sign zones a few times manually during initial configuration, apparently I missed a step in there to purge old keys or something but I cannot see how. Any suggestions?

---

