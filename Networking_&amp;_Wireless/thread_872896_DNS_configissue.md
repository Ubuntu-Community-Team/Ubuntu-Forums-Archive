---
title: "DNS config/issue?"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by g0tb00st on 2008-07-28
Ok, i just installed Hardy (Desktop) LTS on a brand new system, updated and patched it, and then proceeded to install BIND9 using the instructions provided on [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093).

Everything seems to resolve fine on my LAN, forward and reverse lookups are fine. But at this time, I'm having issues resolving names on the Internet, ie "nslookup google.com". Any help would be appreciated.

---

### Post by HermanAB on 2008-07-28
I haven't read the thread you pointed to...

However, what you need is this:
a. The DNS must be set up to do recursive lookups.
b. You have to point it at a higher DNS (Your ISP DNS) to resolve internet names.

Use 'dig' to debug it.

Cheers,

Herman

---

### Post by g0tb00st on 2008-07-28
Herman, 

Thanks for the tip. Can you clarify a few things for me.

1. Recursive lookups - I'm guessing this should be enabled as an option, correct? Do you have specific syntax which I can try and use to insert in my named.conf file?
2. When I'm querying Internet hosts from my DNS and I do nslookup google.com, it resolves fine. It's systems that aren't on the same VLAN as the DNS that cannot resolve Internet host names. I get a "query Refused" message.

I appreciate your assistance!

Erik

> **HermanAB said:**
> I haven't read the thread you pointed to...

However, what you need is this:
a. The DNS must be set up to do recursive lookups.
b. You have to point it at a higher DNS (Your ISP DNS) to resolve internet names.

Use 'dig' to debug it.

Cheers,

Herman

---

### Post by g0tb00st on 2008-07-28
Apparently the "allow-recursion" and "allow-query-cache" options need to be specifically set in Bind9 9.4.1 or newer. I setup BIND9 last year using 9.3.x and had no issues since these options were already set automatically.

Here is a link to Clarification of changes on "allow-recursion" and "allow-query-cache" in BIND 9.4.1 which helped me a great deal!

[http://support.menandmice.com/jforum/posts/list/25.page](http://support.menandmice.com/jforum/posts/list/25.page)

I spent all day on this!!!!! ahhhhhhhh!!!!!!!!!!

Erik

---

