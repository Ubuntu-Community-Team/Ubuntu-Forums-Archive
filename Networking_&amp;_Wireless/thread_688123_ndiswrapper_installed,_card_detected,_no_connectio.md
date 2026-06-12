---
title: "ndiswrapper installed, card detected, no connection"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by reve_etrange on 2008-02-05
I have compiled ndiswrapper 1.52 from source and installed the Broadcom firmware - ndiswrapper reports that the proper hardware is detected - but iwconfig cannot set the ESSID and iwlist scan reports no results.

This is on a Compaq Presario v3000 with a BCM94311MCG (rev 01) wifi card.

Runnig $iwconfig, eth1 appears with wireless extensions.  Following that, I run $sudo iwconfig eth1 essid 'My-AP-name'
I then run $iwconfig again - and the ESSID is still "off/any"
However, $sudo iwconfig eth1 key s:crypt && iwconfig reports that the encryption key is set.
$iwlist scan returns 'no scan results' though there are several networks present.

This is extremely frustrating...I have set up ndiswrapper succesfully many times, compiling from source on my Debian machine and using the Ubuntu GUI tools on friends' laptops, and I have no clue why this time it isn't working.

Can anyone explain this strange behavior or offer a solution?

Thanks!

---

### Post by jan quark on 2008-02-05
you encounter exactly the same problems as I have with ndiswrapper and broadcom 4311

I have to use the fwcutter method and run my broadcom with native drivers

give this a try

[http://janquark.fatfreehost.com/tutorial1.html](http://janquark.fatfreehost.com/tutorial1.html)

---

### Post by hyperair on 2008-02-05
Are you using open or restricted mode? I've noticed that ndiswrapper always tries to use restricted mode if not specified otherwise. Try ```
sudo iwlist eth1 key
``` to check. Don't post the output here unless you want everybody to see your encryption key though.

---

