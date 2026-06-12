---
title: "ping not resolving &quot;unknown host&quot;"
date: 2014-02-19
forum: Networking &amp; Wireless
---

### Post by Vanish00 on 2014-02-19
OS: Ubuntu server 12.04 LTS using via SSH

PROBLEM:
[INDENT]ping google.com
-result: "unknown host google.com"

HOWEVER
ping 74.125.224.72
-result: packets received!
[/INDENT]

I can ping other computer within network and vice-versa. I also think something is wrong with my /etc/resolv.conf since I open it in vim and it is blank. Not sure what to do. Yes, I've checked this problem in other threads but I end up in the same spot.

---

### Post by Iowan on 2014-02-19
Check post #2 here:
[http://ubuntuforums.org/showthread.php?t=1985170](http://ubuntuforums.org/showthread.php?t=1985170)

---

### Post by Vanish00 on 2014-02-19
My issue still remains. I made a few changes to /etc/network/interfaces such as a "dns-nameservers 8.8.8.8 192.168.x.x". I've created a /etc/resolv.conf file but didn't help either.

I do appreciate the help, thanks.

---

### Post by Vanish00 on 2014-02-20
Looks like once I rebooted the computer it finally recognized the DNS server, thank you.

---

### Post by Lars Noodén on 2014-02-20
How are you getting your IP number?  If it is from a DHCP server, that should be passing configuration information with DNS servers.   What does your DHCP server configuration say in regards to 'option domain-name-servers' there?  If that option is empty or wrong, your client will end up with no DNS servers to use in resolv.conf.

Edit: never mind.

---

