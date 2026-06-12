---
title: "Intel PROWireless 3945 unknown after changing kernel"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by Ramus on 2006-09-01
After a standard Ubuntu installation, the wireless card works fine and I can connect wirelessly. But after I install the linux 686 package, the wireless card disappears from the Networking window. When I lspci, I get, at the end:

0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

I've tried to install drivers using ndiswrapper but it just gives me an error:

Installing w39x5
couldn't copy w39x5.inf at /usr/sbin/ndiswrapper line 144.

When I ndiswrapper -l I get:

Installed drivers:
w39x5   invalid driver!

Been trying for a while... any help will be appreciated.

---

### Post by jonwatson on 2006-09-04
I have *exactly* the same problem. It worked for months but I recently decided to reinstall and downloaded the lastest Kubuntu download. Now my wifi only works with a 386 kernel. Once I install the SMP kernel (and associated linux-686-smp) package, it doesn't work.

This looks like a bug to me. Right after the X server thing as well. *buntu's not looking all that tight these days.

/rant

If someone has any info on how to get this working, I'd appreciate it.

---

### Post by ltmon on 2006-09-04
This is due to linux-restricted-modules not being updated for your kernel.  This package has a daemon in it that is required for functioning ipw3945.

See my post in: [http://ubuntuforums.org/showthread.php?t=244814](http://ubuntuforums.org/showthread.php?t=244814)

---

