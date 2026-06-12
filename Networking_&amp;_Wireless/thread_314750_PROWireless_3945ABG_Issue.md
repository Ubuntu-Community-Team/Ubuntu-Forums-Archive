---
title: "PRO/Wireless 3945ABG Issue"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by Forgott3n on 2006-12-08
I have searched before, and I followed [this guide]("http://ubuntuforums.org/showthread.php?p=837922#post837922"). And I made it all the way to the end where I am to "make" and "sudo make install" the driver.

For some reason I get the error method 2 and the compiler quits.

I am using Edgy Eft 6.10 on a Toshiba Intel Centrino Duo with the Intel PRO/Wireless 3945ABG built-in wireless adapter.

Can someone please provide me with assistance?

[EDIT]
Here is some more detail of the error. I first try "make", I get an error saying that the subsystem of ieee80211 was possibly made from an old in-tree (even though I retrieved the latest version) and that to force the build I should set "IGNORE_DUPLICATE_IEEE80211=y" which I did. Upon trying "make" again, I get and error claiming that it cannot find the ieee80211's driver or folder or whatever and that I should try "make patch_kernal" (for the ieee install) or "make IEE80211_INC=/path/to/" for the driver compile.

I tried both options and nothing works. I think this is because I've failed too many times and there are just files whipping around my system.

---

### Post by emdeem on 2006-12-08
You don't need to compile anything - the 3945 drivers are in the Edgy kernel.  Just make sure you install linux-restricted-modules to get the 3945d blob.

---

### Post by Mightyspider on 2007-04-22
Hi there i  get the same problem but the ieee80211 is build in to the kernel and the ipw3945 but i still cant get it working what is the problem then?

---

