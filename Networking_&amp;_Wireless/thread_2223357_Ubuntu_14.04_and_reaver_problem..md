---
title: "Ubuntu 14.04 and reaver problem."
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by tester9 on 2014-05-10
Wireless WPS auditing tool 'reaver' not working on Ubuntu 14.04 (on upgraded from 12.04 as well as on a clean new installation)
Tested on Atheros AR9485 wireless adapter with ath9k modules and some kernels (13.10-13.14).
On upgraded from 12.04 system it even not working with old 3.2 kernels from 12.04 release.

The problem is: reaver failed to associate with any AP with tons of messages like:
[!] WARNING: Failed to associate with xx:xx:xx:xx:xx (ESSID: null)
With association from another application like aireplay-ng reaver starting to work but always failed on the first PIN (even not receiving M1 message):
[+] Sending EAPOL START request
[+] Sending WSC NACK
[!] WPS transaction failed (code: 0x04), re-trying last pin
[+] Trying pin 12345670
[+] Sending EAPOL START request
[+] Sending WSC NACK
[!] WPS transaction failed (code: 0x04), re-trying last pin
and this cycling. On the same AP on Ubuntu 12.04 it runs as well.

Monitor mode is working good. 
Aircrack-ng utilities also runs normaly.
Tested wirth reaver 1.4 and 1.5.

This problem was confirmed by many people on reaver vendor's homepage (used various adapters and tried many tricks to fix this), but all seems to point to new Ubuntu release.

Can anyone help to fix this?
Thanks.

---

### Post by papibe on 2014-05-10
> **papibe said:**
> Thread temporary **closed** for review.

and, after review it will remain closed.

---

### Post by Frogs Hair on 2014-05-10
The use such  of software is not supported on the forums !

---

