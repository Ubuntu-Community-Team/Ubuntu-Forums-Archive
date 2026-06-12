---
title: "Initial wifi connection failing"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by chuck202 on 2017-01-26
A few days ago I posted a thread detailing an issue I was having finding the correct driver for a new machine [https://ubuntuforums.org/showthread.php?t=2350247](https://ubuntuforums.org/showthread.php?t=2350247), since then I've connected to wifi and had no issues, until I power down my machine. When waking up or booting I'm prompted to confirm my wifi password multiple times, I suspect this is because it always fails to connect the first time. After a few hours of searching, I've found that most people who have experienced similar issues have either misconfigured their wifi settings or their driver isn't correct. And so I've made sure that my wifi settings are configured to connect automatically, ticking 'automatically connect to this network when it's available' and 'all users may connect to this network' and then ensuring that the correct password is stored in the security tab. Moving on from the potentially simple fix, I've come up with the following links

[http://cateee.net/lkddb/web-lkddb/WLAN_VENDOR_INTEL.html](http://cateee.net/lkddb/web-lkddb/WLAN_VENDOR_INTEL.html)
[https://wireless.wiki.kernel.org/en/users/drivers](https://wireless.wiki.kernel.org/en/users/drivers)

Sadly, I can't make heads or tails of this and if I were to install another driver without more information it's unlikely I'd get the right one. Do Linux users have a shared repository of information on drivers, or is there any maintained documentation for these sorts of issues apart from Wikipedia? 

Thanks in advance.

---

