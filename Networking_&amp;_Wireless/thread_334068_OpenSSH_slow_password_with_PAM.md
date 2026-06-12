---
title: "OpenSSH slow password with PAM"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by aie93 on 2007-01-08
Recently the password prompt has taken ages to come up when sshing into my Dapper box, all my other boxes work fine and it doesn't seem to be an issue with any of my Edgy boxes either.

I tried changing the authorisation away from PAM but then the shell takes ages to load instead.  Does anyone have any ideas at all?  I found one person on a mailing list archive who seems to have the same problem, but they never got a reply.

It's not really a major issue, but it's very annoying.

Thanks for any help in advance.

---

### Post by aie93 on 2007-01-16
I think I solved it!  The resolv.conf didn't have the local DNS server in it, just remote ones, therefore when it was doing a reverse DNS lookup (at least I assume that's what it was doing) it was taking ages to lookup the IP I was connecting from (192.168.1.*).

I will post again if it hasn't solved it but logged in a few times now.

---

