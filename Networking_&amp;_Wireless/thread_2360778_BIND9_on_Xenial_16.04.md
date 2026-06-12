---
title: "BIND9 on Xenial 16.04"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by ododidit2 on 2017-05-08
Hey,

We just had a Nessus scan and it appears our version of Bind9 has vulnerabilities, the usual apt-get update/upgrade/dist-upgrade doesn't find any update from current version shown below, you can manually download the latest or fixed versions but I have no idea how to manually upgrade without screwing up all the current configuration, I was hoping you could just update the sources.list and do an update but I can't find anything online :(

I upgraded from an old Vivd 14.04 (still have snapshot of that build if it helps) to 15.10 then Xenial 16.04 hoping it would sort it but again the version it moved up to still has these vulnerabilities, any help would be appreciated!

Installed version : 9.10.3-P4-Ubuntu
  Fixed version     : 9.9.9-P5 / 9.9.9-S7 / 9.10.4-P5 / 9.11.0-P2

Thanks!

---

### Post by ododidit2 on 2017-05-09
Sorry meant Vivid 15.04 was original build!

nobody any ideas?

---

### Post by slickymaster on 2017-05-09
*Thread moved to **Networking & Wireless*** for a better fit.

---

### Post by ododidit2 on 2017-05-09
I MAY have found a way of upgrading this manually by downloading latest version and doing custom --configuration etc, will advise if I am successful on the live server which I am NOT looking forward to trying out although I have snapshots to fall back on...

---

### Post by ododidit2 on 2017-05-17
Hey,

No it didn't work, I would have thought that the installed version would have been back-ported with security fixes, how do you go about proving this to an auditor or the nessus scan?

Thanks in advance!

---

