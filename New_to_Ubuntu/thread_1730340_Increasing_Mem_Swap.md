---
title: "Increasing Mem Swap"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by mward69 on 2011-04-15
So Using Ubu's partition on the install, it created 1.5 gig in memory swap. I have 3 gig's...should I increase it to perform faster and if so, how without killing anything on my partition.....I have plenty of space left.
 Please keep in mind I would do better with a point and click GUI than commands  :lolflag:

---

### Post by bodhi.zazen on 2011-04-15
Increasing the size of your swap is NOT going to improve performance.

Swap is space on the hard drive to be used if you run out of RAM, and it is 1,000 x slower then RAM.

In general, most desktop users will not use much more then 1-2 Gb RAM unless you are using virtualilzation or burning a DVD.

In general I do not even use swap if I have much more then 3 Gb of RAM.

If you want a little just in case, use 512 Kb

The only exception is laptops and you want to use hibernation, in that event, you need swap = RAM.

See also : [http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

---

### Post by Chrissd on 2011-04-16
Hi, I agree with everything posted above and personally, for all except one machine, I have swap for absolute dire emergency. If some thing's using swap, some thing&#8217;s wrong. However, it's your computer and you asked for how to do something, hence why I'll point you to a FAQ section.

I appreciate you asked for GUI commands, but I personally do not know of any (no doubt somewhere there is, maybe 'gparted'? It's not the sort of thing you want to be a guinea pig with though)

I would direct you to this page:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I believe it has everything you would want to know about swap.

Best of luck.

---

### Post by 5149.5 on 2011-04-16
This[ link]("http://goo.gl/WQhA") has a lot of swap information. 

Edit: It looks like Cris was a lot faster than me.  My link is the same as his.

---

