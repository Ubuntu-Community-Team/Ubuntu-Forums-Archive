---
title: "Registering hostname to DNS"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by altufaltu on 2008-06-01
I recently installed Ubuntu 8.04 on one of my office PC that had WinXP earlier. I'm having trouble getting its hostname registered with our DNS server. Any help will be appreciated.

I have following lines in /etc/dhcp3/dhclient.conf:
```
send host-name "<hostname>";
send fqdn.server-update on;
```

I tried changing <hostname> above with real one (that too didn't work) but later after browsing forums I found that keeping <hostname> too should work.

I added second line on my own.

I removed hostname from *request* line, but nothing worked.

nslookup still says NXDOMAIN

Network setup seems good as I'm able to share data with other machines on network.

NOTE:
- I do not have any control over DNS server.
- Our IT support team do not support Ubuntu, it is difficult to get help from there.

I have a laptop with WinXP installed, Here is how it is configured:
- IP  address: automatic (DHCP enabled)
- DNS address: automatic
- Default gateways: none
- Append DNS suffixes (in order):
```
domain.company.com
itgate.company.com
company.com
```- Register this connections's address to DNS: checked
- NetBIOS: default

- Altu

---

### Post by altufaltu on 2008-06-12
I'm surprized to see no solution for this!

Oh... where's my WinXP CD???

---

### Post by dmizer on 2008-06-12
have any iptables scripts enabled (like firestarter)?  that could prevent your update from working.

according to this: [http://ubuntuforums.org/showthread.php?t=118612](http://ubuntuforums.org/showthread.php?t=118612)
the fqdn needs a trailing dot like so:
```
send host-name "fqdomain.com**.**";
send fqdn.server-update on;
```

if that doesn't work, take a look at this thread where it talks about ddns scripts:
[http://ubuntuforums.org/showthread.php?t=670374](http://ubuntuforums.org/showthread.php?t=670374)

---

### Post by altufaltu on 2008-06-17
Thanks dmizer, after reading those posts it looks like Windows DNS Server will not register hostname unless I join my Ubuntu box with Active Directory.

I tried a lot of combinations with fqdn settings but no luck.

---

### Post by dmizer on 2008-06-17
> **altufaltu said:**
> Thanks dmizer, after reading those posts it looks like Windows DNS Server will not register hostname unless I join my Ubuntu box with Active Directory.

I tried a lot of combinations with fqdn settings but no luck.

okay, here's a good howto on joining windows active directory: [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

the post is quite old, so take a look at the last 3 or 4 pages of posts and see what people with more recent versions of ubuntu are running into, and what the solutions were, so you can have an idea of what you're up against.

good luck.  i have zero experience with authenticating to active directory.

---

### Post by altufaltu on 2008-06-26
Thanks for your help dmizer, but as I do not want to join my Ubuntu box with Active Directory, I'll keep it as it is for now.

---

