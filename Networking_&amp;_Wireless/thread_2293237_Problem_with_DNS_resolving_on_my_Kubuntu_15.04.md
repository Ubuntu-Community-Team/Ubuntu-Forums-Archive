---
title: "Problem with DNS resolving on my Kubuntu 15.04"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by igor-mironchik on 2015-09-03
Hi.

I connect to Internet router via WiFi. IP and DNS I receive via DHCP. But 50/50 DNS resolving works/doesn't work. My local DNS on 127.0.1.1 can't resolve addresses sometimes.

How to troubleshoot the problem? What can be wrong?

Thank you.

---

### Post by SebastianoS on 2015-09-04
I have the same trouble with Ubuntu, and switching to a wired connection doesn't help. Have you found a solution?

---

### Post by igor-mironchik on 2015-09-04
Hi. I haven't found the solution. If I will find I will tell everybody here.

---

### Post by SebastianoS on 2015-09-04
In my case the situation seems to improve (and I underline improve, still far from perfection) by commenting out with a # the following line

dns=dnsmasq

in /etc/NetworkManager/NetworkManager.conf

---

### Post by igor-mironchik on 2015-09-04
I'm right now on Windows machine. Will look into my Linux one at the evening. Just have one question. Have you seen at the syslog of NetworkManager. May be there some information that can help us.

---

### Post by SebastianoS on 2015-09-04
Nope, but it seems quite a common problem. The thing is everyone seems to be in need of a different solution, I've tried a handful but only delaying the drop of connection without solving it completely

---

### Post by igor-mironchik on 2015-09-04
Hi. I've found the problem and the solution. I've read syslog and found that my router configured DNS via IPv6. And that DNS doesn't work. The solution is simple: disable IPv6 on the connection and reconnect...

---

### Post by SebastianoS on 2015-09-05
Indeed, it seems to be working. I'm only wondering what happened since it was a sudden thing of the last couple of days after months of flawless stability...

---

