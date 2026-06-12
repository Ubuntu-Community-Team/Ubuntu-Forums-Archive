---
title: "StrongSwan:  Moving the private key on a laptop"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by DigiAngel on 2015-02-13
Topic says it...my home dir is encrypted, but the rest of the system is not.  I'd like to move my strongswan private key to my home dir, but I get this when I try:

[  395.889637] audit: type=1400 audit(1423883465.296:37): apparmor="DENIED" operation="capable" profile="/usr/lib/ipsec/charon" pid=3495 comm="charon" capability=1  capname="dac_override"
[  395.889649] audit: type=1400 audit(1423883465.296:38): apparmor="DENIED" operation="capable" profile="/usr/lib/ipsec/charon" pid=3495 comm="charon" capability=2  capname="dac_read_search"

Not gonna lie I'm clue free on dealing with apparmor...how do I allow charon access to my home dir?  Thanks all.

---

