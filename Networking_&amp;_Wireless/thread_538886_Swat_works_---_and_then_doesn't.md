---
title: "Swat works --- and then doesn't"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2007-08-30
Well, I had swat running, and then I installed vmware-player and it de-installed swat (why, I'm not sure).

Then I did:

sudo apt-get install swat

However this time around, as opposed to install netkit-inetd it install openbsd-inetd.

Why I'm not sure.

However now when I open up to [http://127.0.0.1:901](http://127.0.0.1:901) I don't get swat anymore...


Any ideas why this changed?

Also, how do resolve it no longer responding.

---

### Post by mohnkern on 2007-08-30
After much use of apt-get I finally seemed to hit the right combination to get swat to work.  I deinstalled swat, deinstall openbsd-inetd, installed netkit-inetd and tcpd and then swat.


At least that's close to what I did.

---

