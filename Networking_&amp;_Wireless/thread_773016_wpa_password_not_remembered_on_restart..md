---
title: "wpa password not remembered on restart."
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by litdie on 2008-04-28
the title pretty much sums it up.

i installed ubuntu thru wubi and everything is working great. 100%

my wireless works fine, if and only if, after each reboot i go to network manager and enter my wpa password.

i have to go to manual setting and edit my wifi setting and delete and readd my password each reboot.

ive tried saving the configuration, but it still doesnt work.


any idea?

dell 9300
ipw2200
wpa.

---

### Post by Alldan on 2008-04-29
I had the same problem in Gutsy and now in Hardy Heron too.
My configuraton: Acer 5100 / Atheros wireless card an another computer with sis163u USB dongle (working with ndiswrapper) The restricted Atheros driver and ndiswrapper works perfectly but i need to re-enter wpa2 password at each boot. I encounter this problem on both computers.

Solution:
1 i installed wicd from here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) (all installation information is here)
2 restart
3 reenter wireless password in network setup utility and verify connectivity (at this time wicd applet will show network activity)
4 enter wireless password in wicd utility in advanced settings and check "automatically connect"

After restart wireless started without problem for me

Observation: network-manager is removed and replaced with wicd

---

### Post by TOM_C_A_T on 2008-05-28
thanks this solved my prob !!

---

