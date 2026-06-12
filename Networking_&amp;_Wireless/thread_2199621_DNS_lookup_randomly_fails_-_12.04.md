---
title: "DNS lookup randomly fails - 12.04"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by greyoracle on 2014-01-14
I've had this problem for a long time, and I'm not sure what originally caused it, but my connection will randomly stop working and it will say the DNS lookup failed.  This happens on at least two different wireless routers (my house and a local coffee shop).  I've lived with it for a long time by turning on wireless and turning it off again, which restores functionality.  The problem tends to happen a lot more often when I'm actively downloading something using qbittorrent, although it can happen when all of my torrents are not actively seeding and I'm not downloading anything.

Any help with this problem would be greatly appreciated.  Thanks.

---

### Post by Kirboosy on 2014-01-15
Perhaps setting a static public DNS server might help? Try using Google's DNS servers. 8.8.8.8 or 8.8.4.4 
[URL="https://developers.google.com/speed/public-dns/"]
Google Public DNS[/URL]

Hope that helps!
~Caboose

---

### Post by Beach_Geek on 2015-01-12
On your own router, check for an "IP Flooding" option in Security/Firewall section.  We've found this option needs to be disabled on the modem/routers provided by COX Cable and Mediacom.
When connecting to routers you don't have control over, you'd have to adjust settings of OS or qbittorent so the firewall doesn't falsely detect a IP Flood attack.
Hopefully someone will have a suggection on what settings would help.  Only settings we've reduced are max connections and max half-open connections for qbittorrent.

Hope this helps someone,
BG

---

