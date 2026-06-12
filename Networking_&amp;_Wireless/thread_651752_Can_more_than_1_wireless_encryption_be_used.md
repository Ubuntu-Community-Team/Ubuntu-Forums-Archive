---
title: "Can more than 1 wireless encryption be used?"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by newnet on 2007-12-27
Say I want to use WPA and another computer want to use WEP. Can this be done in the same router?  Or must all computers connected to the same router use the same type of encryption?

---

### Post by Junglizer on 2007-12-27
It would have to be one type of encryption per router, it could be done, with both but you'd have to have a seperate system to re-encrypt all of the traffic which would create great latencey issues, and is a bit out of the scope of these forums. Also, why do you want to use 2 seperate encryptions? Why not just use WPA2 Enterprise for both, one of the newest encryption methods for wireless to date.

---

### Post by newnet on 2007-12-27
> Also, why do you want to use 2 seperate encryptions? Why not just use WPA2 Enterprise for both, one of the newest encryption methods for wireless to date.
Because WPA2 is not well supported for Linux.  Different drivers require different configurations to get the encryption to work.  I tried with 3 different cards already.  None of them will work with WPA2.

It is not fun buying new cards, nor is trying different how-tos, nor is repeatedly editing /etc/network/interfaces.

---

