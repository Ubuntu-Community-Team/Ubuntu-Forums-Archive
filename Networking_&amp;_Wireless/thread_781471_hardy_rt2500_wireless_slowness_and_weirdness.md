---
title: "hardy rt2500 wireless slowness and weirdness"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by dubstar on 2008-05-04
ok been experiencing the reported slow wifi with my rt2500 based wifi card on the lappy after upgrading to heron, no fix's have worked under ubuntu.

just went into xubuntu (XFCE) and the wifi is now back up to speed.....

and ideas why the hell? 


:confused:

---

### Post by ifknot on 2008-05-09
did the ubuntu upgrade gutsy -> hardy

wifi wierdness ensued 4M -> 2M -> 1M -> .5M -> .2M WTF???

fresh install hardy

same problem :(

tried your xubuntu idea

same problem :(

"hardly heron" more like

went back to gutsy gibbon

4M!

:)

---

### Post by ZeroXtreme on 2008-07-19
If you haven't found the solution yet, try the following:

1. sudo iwconfig wlan0 rate 54M
2. add a preup line in your /etc/network/interfaces file so the changes are permanent

---

