---
title: "SynCE with Ubuntu questions"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-29
I'm trying to get my Treo 800W (Windows Mobile 6.1) to sync with a pretty fresh install of Ubuntu (ubunu Newbie here).

I've found a page that seems to walk me through it, but I'm stumped on a particular part.

Here's the page:
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

and I'm stumped when it says to put the following in Terminal:

```

/sbin/ifconfig -a | grep 80:00:60:0f:e8:00  | cut -d " " -f 1
```

I do this, but absolutely nothing comes back, just another Terminal prompt. 
Is this the expected behavior?

Thanks in advance!

---

### Post by JDuc on 2008-12-29
Figured it out, it's just wanting to know what the network connection is called, in my case: Eth2

---

