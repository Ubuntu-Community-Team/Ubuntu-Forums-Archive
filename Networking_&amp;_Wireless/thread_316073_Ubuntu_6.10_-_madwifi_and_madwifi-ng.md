---
title: "Ubuntu 6.10 - madwifi and madwifi-ng?"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Striatum on 2006-12-10
Hi all!

I heard Ubuntu 6.10 (restricted modules) ships with madwifi AND madwifi-ng, is this correct?
If yes, which one is installed by default and how can I change to the other one?

Thanks!
Dominik

---

### Post by spd106 on 2006-12-10
I thought edgy only had the ng drivers. I suppose they might still be the old ones if you upgrade from dapper, iirc dapper had both ath_hal and new_ath_hal etc.

The only way I know to check is **dmesg | grep ath**, if it has ath_pci version 0.9.2 then it's the recent madwifi-ng. Still waiting for a security update to 0.9.2.1, shouldn't be too long.

I suppose checking ifconfig for the wifi0 interface might tell you the same. I'm quite sure this wasn't there in the old release. 

If you wan to be sure that you have the latest release then download it from [http://www.madwifi.org](http://www.madwifi.org) and compile it yourself. There are some guidelines in the distribution specific pages.

---

