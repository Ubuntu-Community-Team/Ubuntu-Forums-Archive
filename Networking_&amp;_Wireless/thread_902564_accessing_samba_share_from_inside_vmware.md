---
title: "accessing samba share from inside vmware"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by dreaminhere on 2008-08-27
I've setup samba following this howto [http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640).  However, I can't connect from windows xp pro from inside vmware on the same box.  When I run ifconfig I get 

          inet addr:169.254.9.222  Bcast:169.254.255.255  Mask:255.255.0.0
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet addr:75.200.14.161  P-t-P:66.174.168.64  Mask:255.255.255.255
          inet addr:172.16.101.1  Bcast:172.16.101.255  Mask:255.255.255.0
          inet addr:192.168.78.1  Bcast:192.168.78.255  Mask:255.255.255.0

When I ping from windows I get a timeout for 169... and unreachable for the last 3.  the 127... pings but it doesn't like my username and password when I try to map it.  I think the one I should be trying to map to is the 169.254.9.222 number, but it always times out.


Any ideas?

---

### Post by dreaminhere on 2008-08-27
Figured it out from another post somewhere else.

I changed the networking from bridged to nat and it is working with the 169.254.9.222 address. FINALLY.

---

