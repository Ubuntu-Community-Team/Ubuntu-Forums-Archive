---
title: "Samba through Windows XP firewall ?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by celem on 2008-06-01
My Xp built-in firewall interferes with proper Samba operation. If I turn off the firewall Samba works. Oddly, it even works for a while after I turn the firewall back on. I suspect that it has to do with the File and Printer Sharing firewall exception list, which exempts TCP 139 & 445, and UDP 137 & 138. I examined the firewall log (C:WINDOWS\pfirewall.log) and SAMBA uses ports 139 & 137 as both destinations and sources in combination with ports 3878, 3879, 3880, 3881, 3882, 3909, 3910, 3911, 3912. 3913, 3946, 3947, 3948, 3949, 3950, 46738, 46742 and others.

Does anyone know how to set up the Windows XP built-in firewall so that Samba will work when the firewall is active?

P.S.: Yes, I know that this is a Linux forum, not a Windows forum, but who better to have the answer. After all, the Windows folks don't understand Samba.

---

### Post by jetsam on 2008-06-07
Strange.  I've never had to do anything to the Windows XP firewall but allow the default file-sharing exceptions when I turn on file and print sharing.  

Thanks for the tip on the XP firewall log.  I didn't know about that.  Now that I do, I see I also get some blocked Samba traffic in the high port ranges as well, but Samba and XP seem to function fine regardless.   

Only thing I can think to check-- double check the scope of your file sharing exceptions in the XP firewall.  If it's set to "My Network (subnet) only", double check your subnet mask with ipconfig from the Windows command line and make sure it's set correctly and that both machines are on the same subnet.

---

### Post by celem on 2008-06-11
Thanks for the suggestion. My local network is 192.168.0.1-255 and the mask is 255.255.255.0. This issue is a puzzle to me?

---

