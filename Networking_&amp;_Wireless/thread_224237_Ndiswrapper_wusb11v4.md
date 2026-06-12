---
title: "Ndiswrapper wusb11v4"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by SigmaX on 2006-07-27
Yo.  Taking a shot at ndiswrapper with my WUSB11v4 linksys adapter.

```
$ lsusb
Bus 001 Device 006: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
```

So it exists... that's a start.

I found a thread on LinuxForums [here]("http://www.linuxforums.org/forum/ubuntu-help/60569-installing-wireless-client-wusb11v4-2.html#post351972") which shed hope on the subject, telling me everything would be nice and jiggy if I simply installed a later version on ndiswrapper.  I assume the original poster was on Breezy (I'm on Dapper), but he got it working.  I compiled the latest ndiswrapper, and even tried the svn, but as you can see I still get nothing:

```
$ ndiswrapper -l
Installed drivers:
wusb11v4        invalid driver!

```

The driver was extracted from [ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe]("ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe") using wine.

Any tips would be greatly appreciated.

SigmaX

---

### Post by SigmaX on 2006-07-28
bump.

---

### Post by SigmaX on 2006-08-26
For the record:  The problem was that I was trying to install the single .inf file alone.  You must run ndiswrapper -i *while in* the driver directory, so it can reference the other data files included.

SigmaX

---

