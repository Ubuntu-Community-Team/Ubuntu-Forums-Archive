---
title: "DNS Server keeps changing"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by Innova on 2007-03-01
I have a Linksys router, that uses DHCP.

Occasionally I have problems connecting to certain sites.  It seems to be related to my DNS server.  When I use the DNS servers of my ISP, things work fine.  However, the DNS server keeps switching back to 192.168.1.1.  When that happens, there are a lot of sites that won't resolve.

How can I make it so my DNS server is always my ISPs?

---

### Post by symbo978 on 2007-03-03
Hi Innova, I have the very same problem. The DNS address keeps reverting to the router address, even when still in use. Have checked the documentation with no luck. If I find out how to fix it I will let you know.

---

### Post by Innova on 2007-03-03
Thanks, mine is still getting reset also.  If I figure it out, I will also post back.

---

### Post by Innova on 2007-03-11
No one has an idea on this?

---

### Post by 454redhawk on 2007-03-11
> **Innova said:**
> I have a Linksys router, that uses DHCP.

Occasionally I have problems connecting to certain sites.  It seems to be related to my DNS server.  When I use the DNS servers of my ISP, things work fine.  However, the DNS server keeps switching back to 192.168.1.1.  When that happens, there are a lot of sites that won't resolve.

How can I make it so my DNS server is always my ISPs?

[http://www.ubuntuforums.org/showpost.php?p=1960622&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1960622&postcount=7)

---

### Post by Mr. C. on 2007-03-11
The solution posted by that link is flawed.  Root can overwrite or remove files, and it is not the correct way to solve this problem.

You need to make the DNS changes in your router, which I presume is also your DHCP server.  Make the correction there, and your DHCP clients will pick up the correct DNS servers.

MrC

---

### Post by Innova on 2007-03-11
> **Mr. C. said:**
> The solution posted by that link is flawed.  Root can overwrite or remove files, and it is not the correct way to solve this problem.

You need to make the DNS changes in your router, which I presume is also your DHCP server.  Make the correction there, and your DHCP clients will pick up the correct DNS servers.

MrC

My router is set up to use my ISPs DNS servers, but my machine keeps reverting back to the router...when this happens a lot of lookups fail...

---

### Post by Mr. C. on 2007-03-11
> **Innova said:**
> My router is set up to use my ISPs DNS servers, but my machine keeps reverting back to the router...when this happens a lot of lookups fail...

Yes, I understand that lookups will fail.  However, I don't believe your router is configured correctly.  You need to disable its internal DNS caching server.  Can you take some screenshots of the DNS setup page?  Or tell me the exact brand / model of your router?

Let's get something straight - the system does not change itself back by itself - it is being told by your router to do so.  You can either fix the router configuration, or you can force the DNS servers another way.

MrC

---

### Post by 454redhawk on 2007-03-12
> **Mr. C. said:**
> The solution posted by that link is flawed.  Root can overwrite or remove files

MrC

You are incorrect in this case and that solution works like a champ.

man chattr

[b]A  file  with  the `i' attribute cannot be modified: it cannot be deleted or renamed, no link
       can be created to this file and no data can be written to the file[/b].  Only the [COLOR="Red"]superuser[/COLOR] or  a
       process possessing the CAP_LINUX_IMMUTABLE capability [COLOR="Red"]can set or clear this attribute[/COLOR].

---

### Post by Mr. C. on 2007-03-12
Yes, you are correct.  chattr must be reversed.

My point was aiming towards hard coding values in /etc/resolv.conf in such a fashion, when the goal is to use the ISPs DNS servers offered via the DHCP server.

The correct solution in my opinion is to resolve the matter, not place a hardened shield over it.

Thanks for pointing this out.
MrC

---

### Post by 454redhawk on 2007-03-12
> **Mr. C. said:**
> Yes, you are correct.  chattr must be reversed.

My point was aiming towards hard coding values in /etc/resolv.conf in such a fashion, when the goal is to use the ISPs DNS servers offered via the DHCP server.

The correct solution in my opinion is to resolve the matter, not place a hardened shield over it.

Thanks for pointing this out.
MrC

I had this same problem and gave up trying to figure it out after a significant amount of time. My router appears to be setup correctly.

If there is a better or more correct way I would use it. I just dont know how to "correctly" fix it.

---

### Post by scxtt on 2007-03-12
> **Innova said:**
> I have a Linksys router, that uses DHCP.

Occasionally I have problems connecting to certain sites.  It seems to be related to my DNS server.  When I use the DNS servers of my ISP, things work fine.  However, the DNS server keeps switching back to 192.168.1.1.  When that happens, there are a lot of sites that won't resolve.

How can I make it so my DNS server is always my ISPs?are you setting the DNS servers manually in /etc/resolv.conf?  do they only get switched back after reboot?  do you have the package **resolvconf** installed? (do a **sudo aptitude search resolvconf** to find out)

---

### Post by Mr. C. on 2007-03-12
> **454redhawk said:**
> I had this same problem and gave up trying to figure it out after a significant amount of time. My router appears to be setup correctly.

If there is a better or more correct way I would use it. I just dont know how to "correctly" fix it.

Sometimes a hammer is the only tool that works.

Many routers come with internal DNS caches, that are very poorly implemented.  They give their own IP as the DNS server, and then forward requests to your ISPs DNS server(s) when not found in the cache.  They simply do not have enough memory to be a good DNS cache, and don't seem to handle error conditions well.  Thus failing, and causing long timeouts.

The key is to disable the router's internal DNS service, so that your ISPs DNS servers are passed through correctly during the DHCP request.

Another alternative is to use your own Ubuntu box itself as a caching-only DNS server.  Look ups then remain local once data is in the cache, and are very fast.

MrC

---

### Post by dmizer on 2007-03-12
here's what i've used on many occasions. [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

and even better, it doesn't require a hammer ;)

---

### Post by Innova on 2007-03-12
> **Mr. C. said:**
> Yes, I understand that lookups will fail.  However, I don't believe your router is configured correctly.  You need to disable its internal DNS caching server.  Can you take some screenshots of the DNS setup page?  Or tell me the exact brand / model of your router?

Let's get something straight - the system does not change itself back by itself - it is being told by your router to do so.  You can either fix the router configuration, or you can force the DNS servers another way.

MrC

Thanks for helping out.  

I thought I had the router set up correctly, but it wouldn't surprise me one bit if I have something wrong.   I am at work now, so I can't take screen shots, but it is a Linksys WRT54G if that helps at all.

---

### Post by Mr. C. on 2007-03-12
> **Innova said:**
> .. Linksys WRT54G if that helps at all.

It does;  unfortuantely, there are 9 different models of that product.  If you can find the version number (eg. v2) that would be perfect.

MrC

---

### Post by Innova on 2007-03-12
> **Mr. C. said:**
> It does;  unfortuantely, there are 9 different models of that product.  If you can find the version number (eg. v2) that would be perfect.

MrC

Firmware Version: v1.00.9 

Also, here is a screenshot:

[http://img361.imageshack.us/img361/7079/wrt54ged4.png](http://img361.imageshack.us/img361/7079/wrt54ged4.png)

---

### Post by Mr. C. on 2007-03-12
Innova,

That's the firmware version.  The model version will be on the tag on the bottom of the unit.

MrC

---

### Post by Innova on 2007-03-12
> **Mr. C. said:**
> Innova,

That's the firmware version.  The model version will be on the tag on the bottom of the unit.

MrC

ver.6

---

### Post by Mr. C. on 2007-03-13
Innova,

You should update your firmware for the router to version 
 1.02.0; this firmware resolves several DHCP issues, and many other problems:

- Resolves issue with IP address assignment via DHCP on some particular devices.
- Resolves DHCP server issue.

Update, reboot the router, and then see how things work out.
MrC

---

