---
title: "No internet Ubuntu 16.04"
date: 2017-07-08
forum: Networking &amp; Wireless
---

### Post by avents on 2017-07-08
My dual boot laptop lost both wired and wifi, apparently after the latest kernel update/upgrade which showed errors, done while abroad. 
 Window 10 is working (both wired and wireless). 
It looks like I'll need to re-install or just try to boot in a previous kernel (don't really know how to do this ).
I'd like to provide more info but everything I tried requires internet .

---

### Post by jeremy31 on 2017-07-08
If you have dual boot the grub menu should appear while booting it up.  Scroll to advanced options, then you should see a screen with installed kernels, scroll down to the old one and press enter.  Once booted into the old kernel check ```
dpkg -l | grep linux-image
```
See if you have a linux-image-extra with the same version as the newest linux-image

---

### Post by avents on 2017-07-08
:~$ dpkg -l grep linux-image
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  grep           2.25-1~16.04 amd64        GNU grep, egrep and fgrep
un  linux-image    <none>       <none>       (no description available)

---

### Post by avents on 2017-07-08
In synaptic I can remove the latest linux-image-4.4.0-83-generic. But should I use 'Mark for Removal' or 'Mark for Complete Removal' ?  
Thanks

---

### Post by avents on 2017-07-08
In synaptic I ran upgrade and everything seems to have fixed itself
Thanks again

---

