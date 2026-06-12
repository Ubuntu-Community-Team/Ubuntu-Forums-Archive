---
title: "firefox issue"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-10-11
Hey there,

I just installed Xubuntu Karmic on my Dell Mini 9. After following the instructions on [http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html](http://www.ubuntumini.com/2009/10/ubuntu-910-karmic-koala-beta-is.html), I got the Broadcom wireless card working.

However, whenever I go to just about any network address, Firefox reports "Looking up http://www.google.com/" or whatever address I put in. It gets really annoying for any site that uses doubleclick or any other ad server (so, it takes a long time for just about any page to load.

My download speeds are normal, however. It just takes time for the page to begin loading.  Anything I can do to fix or work around this problem?

Thanks,

--Red

---

### Post by Soulcage on 2009-10-11
I don't know it will solve your problem, but you can try typing about:config in the address bar then paste network.dns.disableIPv6 in the filter then double click it and restart firefox.

---

### Post by leomelo on 2009-10-11
Use Chromium.

---

### Post by sandyd on 2009-10-11
use OpenDNS.

---

### Post by Redmage913 on 2009-10-11
Forgive me, but I do not understand how OpenDNS could help me. (Then again, I know little about networking tools.)

I like Firefox, and would prefer to keep using it.

Also, I changed the boolean in about:config to true and it didn't seem to help.

---

### Post by richaoj on 2009-10-11
What it sounds like is that your nameservers are taking a long time for a lookup.  You can manually set your dns servers.

OpenDNS's nameservers are 208.67.222.222 and 208.67.220.220.

[www.opendns.org](www.opendns.org)

Also, you can use the Adblock Plugin for firefox, which should reduce the adserver lookup problem, as it blocks ads.  Go to Tools: Addons in firefox.

---

### Post by Redmage913 on 2009-10-11
Wow, that really seemed to speed up initial page loading, even from what I had before I installed Karmic.

Thanks a lot.

---

