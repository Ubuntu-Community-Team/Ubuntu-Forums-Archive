---
title: "Slow surfing with wrt54gl linksys router"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by cchevy on 2008-05-22
Hello!

I read all about this and tried everything but still can't fix this problem. I have this with the wired internet connection(haven't checked for wireless).

While my colleague's internet on XP is like a bullet(and he is laughing at me), I tried several options that I read in the forums. 

I disabled ipv6 in Firefox, placed lines in aliases:

 /etc/modprobe.d/aliases

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off
blacklist ipv6
```


and still nothing.

Using 7.10. Using DHCP. Rounter Firmware Version: v4.30.11

Downloads are going at max speed. I just can't get the best out of surfing websites.

Can somebody please tell me what the problem is?

p.s. Tried the 8.04 live cd, but still the same...

---

### Post by dmizer on 2008-05-22
the method you used to disable ipv6 is ancient.  please use this method:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

also, try using opendns servers:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

if that doesn't get you up to speed, post back.

---

### Post by cchevy on 2008-05-23
Thanks man. That worked for me!

---

### Post by tedrogers on 2009-07-14
Yeah me too...really speeded things up.

Dunno if I managed to blacklist ipv6 properly though, some of the tutorial wouldn't work, maybe as I'm using 9.04 and the tutorial listed only goes up to 8.04.

The bit about 'aliasing net-pf-10 to off' failed for me. :(

Just used the section above to blacklist ipv6.

How do I know it's working though?

---

