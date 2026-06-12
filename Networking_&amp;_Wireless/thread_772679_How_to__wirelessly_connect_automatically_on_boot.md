---
title: "How to  wirelessly connect automatically on boot"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by udoko on 2008-04-28
Went to 7.10, wireless works great, but need the command to be online when booting up.
Thanks
Had it before but lost the info.

---

### Post by Alldan on 2008-04-28
I had the same problem in Gutsy and now in Hardy Heron too.
My configuraton: Acer 5100 / Atheros wireless card an another computer with sis163u USB dongle (working with ndiswrapper) The restricted Atheros driver and ndiswrapper works perfectly but i need to re-enter wpa2 password at each boot. I encounter this problem on both computers.

**Solution**:
 1 i installed wicd from here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) (all installation information is here) 
 2 restart
 3 reenter wireless password in network setup utility and verify   connectivity (at this time wicd applet will show network activity)
 4 enter wireless password in wicd utility in advanced settings and check "automatically connect"
  
After restart wireless started without problem for me

Observation: network-manager is removed and replaced with wicd

---

