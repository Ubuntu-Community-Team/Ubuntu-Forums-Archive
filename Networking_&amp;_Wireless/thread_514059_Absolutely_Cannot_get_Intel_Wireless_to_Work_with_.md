---
title: "Absolutely Cannot get Intel Wireless to Work with Feisty"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by mattmueller on 2007-07-31
Ok, so I recently got a new laptop... Dell Latitude D830 with Intel 4965 WLAN (802.11a/g/n) mini Card.  

I originally had some problems getting nvidia and x up and running and all that good stuff when installing feisty (aside from having to install with the alternate cd due to another error), but I got everything working perfectly....only to discover my wireless card was not working.

I have tried everything I could find, downloading and compiling various versions of ieee and ipw3945, so much so that I have twice reinstalled thinking I might have screwed stuff up in the kernel.  My most recent attempt was to use an old Dapper installer script for ipw3945...didn't work either.  Whenever I modprobe ipw3945 I get the following error:

```
matt@ubuntulappy:~$ sudo modprobe ipw3945
FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sh: /sbin/ipw3945d: not found
FATAL: Error running install command for ipw3945
```

Does anyone have any idea what I could be doing wrong/how I can get feisty to recognize my card?  I know support is supposed to be built in in 7.04 but apparently it's not...

Thanks in advance for any help.

---

### Post by dannyboy79 on 2007-07-31
have ytou tried this: [http://ubuntuforums.org/showthread.php?p=3097541](http://ubuntuforums.org/showthread.php?p=3097541)

also, I am not sure why you're trying to load an ancient ipw3945 driver when you have the 4965. good luck

---

