---
title: "Bizzarre Internet  Access Problem"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by okok on 2006-10-25
There was a problem with my ADSL modem and it was replaced by the provider. Its connection type is pppoe. Since then, I can access all websites normally when I use Windows, but when I use Ubuntu, either on the same machine (a dual boot machine), or from another machine running ubuntu, some websites are available, while with others, the browser just waits for some sites to load forever, while some sites are accessible. I CAN succesfully ping even the ones I can't access. The inaccessible ones aren't accessible via browsers, e-mail clients or IM clients, so this is not a browser problem.

Again, the problem is the same with two diffrent machines running Dapper, which had performed perfectly before the modem change. But when I run windows, everything is accessible.

Any idea what the problem might be and how to solve it?

---

### Post by lag1980 on 2006-11-29
> **okok said:**
> There was a problem with my ADSL modem and it was replaced by the provider. Its connection type is pppoe. Since then, I can access all websites normally when I use Windows, but when I use Ubuntu, either on the same machine (a dual boot machine), or from another machine running ubuntu, some websites are available, while with others, the browser just waits for some sites to load forever, while some sites are accessible. I CAN succesfully ping even the ones I can't access. The inaccessible ones aren't accessible via browsers, e-mail clients or IM clients, so this is not a browser problem.

Again, the problem is the same with two diffrent machines running Dapper, which had performed perfectly before the modem change. But when I run windows, everything is accessible.

Any idea what the problem might be and how to solve it?

I am having the exact same problem... and it is only on my wireless connection at home.  If I connect with a wired connection there is no problem and using the wireless on my school campus is no problem.  Windows machines can connect just fine on my home wireless network, but not Ubuntu.  If anyone has found a solution please let me know.

Thanks.

---

### Post by albesan on 2006-11-29
hello guys,
I don't really know what I am talking about but I think this might help:

[http://ubuntuforums.org/showthread.php?t=53112](http://ubuntuforums.org/showthread.php?t=53112)

---

### Post by okok on 2006-11-29
Yes, disable IPv6. Here is how:
[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

### Post by mikey3000 on 2006-11-29
I had the same problem after re-installing 5 times I finally figured out I had to update my firmware on my modem ,After that It worked just fine.

---

### Post by stream303 on 2006-12-01
Common problem when swapping out a new dsl modem.

Quickest tip is to place your isp's primary and backup nameservers into your router's setup page.

If that doesn't work, you can make an edit to one line with those isp dns addresses and be back in business.

I wrote a quickie howto since it comes up a lot.  Frustrated me for sure!

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

