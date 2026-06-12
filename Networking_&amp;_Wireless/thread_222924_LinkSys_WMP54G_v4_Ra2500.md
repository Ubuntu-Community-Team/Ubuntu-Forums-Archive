---
title: "LinkSys WMP54G v4 Ra2500"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by ericcmi on 2006-07-25
I have Dapper 6.06 AMD64, the ISO from the main site, and a WMP54G ver4 which is thhe Ra2500 chipset.

I installed the os just fine and got the wireless working with WEP only once I was running from the hard drives.


All I had to do was go into NetworkTool and setup the key and all was well.

However, after a series of tries at installing XGL+Compiz my X config was getting rather sloppy. So I just formatted figuring everything would go as previously.

As it tunrs out after a reinstall(with both ext and swap formatted) the same default ra2500 driver is not working.

```


root@AMD64:~# dmesg | grep ra0 [ 91.385956] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !


```

That is the error I get in dMesg and the ra0 device does not show up in the NetworkTools.

Could some one tell me how to fix this? I want to install the better ra2x00 driver on the wiki, but i think i need to install some packages first, But this is difficult with out working ra2500 wireless drivers.

thanks in advance.

im editing this to clarify: On the first install, wireless worked out of the box, no config necessary(except wep key). On each install attempt therafter, the ra0 wireless does not show in the NetworkTools and is NOT working.

---

