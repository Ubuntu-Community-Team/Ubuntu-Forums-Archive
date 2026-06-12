---
title: "[SOLVED] interfaces problem"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by d_in_Conduct on 2007-11-10
I'm seeing some errors reading /etc/network/interface.  Problem is, I can't fix them.

If I type "tail /etc/network/interface" I can clearly see what's wrong.  But if I type "sudo gedit /etc/network/interfaces" I see a completely different file.  I fixed the errors there yesterday, but the system isn't seeing the file.

slocate shows only /etc/network/interfaces and /etc/network/interfaces~, but neither of those resembles what the system is apparently seeing.  Is there a cached version of this file somewhere that is taking precedence?

---

### Post by Seisen on 2007-11-10
You should only have a /etc/network/interfaces file, did you create the /etc/network/interface file or something? Also have you tried tail /etc/network/interfaces.

---

### Post by d_in_Conduct on 2007-11-10
I found the problem.

/etc/network/interfaces had grown really long with about 30 blank lines between what I was seeing with gedit (the top part, most of the text) and with tail (the bottom part, where the errors were).  So I fixed that and all is well.

---

