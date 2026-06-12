---
title: "ipw2200 wireless issues after Gutsy update"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by sunrocks on 2008-01-15
Last night, I updated my laptop (Toshiba Tecra M2) via my wireless connection (eth1, which is an onboard Intel(R) PRO/Wireless adapter).  After the update, wireless ceased to function.  The dmesg output reported this:

[   18.112000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   18.112000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.112000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.316000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   19.316000] ipw2200: Unable to load firmware: -2
[   19.316000] ipw2200: failed to register network device
[   19.316000] ipw2200: probe of 0000:02:05.0 failed with error -5

so I decided after doing some internet searching to try this:

[http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/](http://untitledfinale.wordpress.com/2007/10/22/update-ieee-80211-and-ipw2200-on-ubuntu-gutsy/)

I updated both the ieee stuff and the ipw2200 driver.  Now  I get this:

dmesg|grep ieee
[    5.776000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00003900006111f7]
[   18.268000] ieee80211_crypt: disagrees about version of symbol struct_module
[   18.504000] ieee80211: disagrees about version of symbol struct_module
$ dmesg|grep ipw
[   18.656000] ipw2200: disagrees about version of symbol struct_module

I've done several make cleans, and make, make install's to try to get this cleaned up, but to no avail.  Can anyone help me figure this mess out?

R

---

### Post by Hightide on 2008-01-18
You may find Gilf's thread helpful

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

:)

---

### Post by Mach1US on 2008-02-25
Same deal here.
I posted my configs here too :
[http://ubuntuforums.org/showthread.php?p=4399532#post4399532](http://ubuntuforums.org/showthread.php?p=4399532#post4399532)

---

