---
title: "Is there a way to permanently cache DNS resolves ? (even after reboot)"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by verb3k on 2007-12-28
Hi,

I've followed the instructions here [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)  and it seems working fine but after I reboot, all cached IPs will be gone. Is there a way to make them sticky? 

Thanks in advance,
verb3k

---

### Post by AJB2K3 on 2007-12-28
I would like to know this as EVERYTHING I have tryed has failed to give realible network access.
I'm even contemplating returning to XP

---

### Post by verb3k on 2007-12-28
Please guys do me a favor and let me know if you have a solution.

---

### Post by arvevans on 2007-12-28
You could do specific DNS resolves and then enter that into /etc/resolv.conf, but this is not recommended.  What if the service you are trying to access changed it's host IP...then you would be locked out from that service by virtue of your now erroneous resolves.

From the command line do "man resolv.conf" to see how this file works.
From the command line do "man dig" to see how to do manual DNS resolves.

Arv
_._

---

### Post by arvevans on 2007-12-28
After thinking about this some more, there is another solution that might work.  You already have Primary and Secondary DNS servers.  You could set up your own computer to be a Tertiary DNS server.  With this running you could control your own cache interval and thus have frequently used URL-to-IP resolves stored locally.  The setup would be a bit strange because you would use your own IP address for primary DNS queries and the DNS server would then use your regular primary & secondary DNS servers to get its resolves.  But, it should work.

A local or Tertiary DNS server capability could also available via a local WiFi Router/Hub if you have one of those and a Local Area Network ( LAN) between your computer and your Internet access.

Arv
_._

---

### Post by zazuge on 2008-01-30
yes there is "pdns" see:
[http://ubuntuforums.org/showthread.php?t=331850&highlight=DNS+cache](http://ubuntuforums.org/showthread.php?t=331850&highlight=DNS+cache)

---

