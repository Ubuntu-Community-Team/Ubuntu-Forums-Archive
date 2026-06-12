---
title: "ssh and web connections dropping"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by cntrtrst on 2008-10-27
I have an odd problem.  My ssh and web connections are frequently being dropped.  During these events, I can hear the hard drive spinning (I think.  it may be something else.  sort of a rattle), sometimes the system pages, and then the ssh freezes and if a web site is in mid-download it hangs.  

I tried running 'top' to see if I could catch some process in the act of blowing out my connections, but I never saw anything.  Seems like some kind of low level process that barely registers is somehow causing this.

any help appreciated.

---

### Post by cntrtrst on 2008-10-27
I figured out the process, but still don't know what's really happening.  The process is the rss reader for firefox.  whenever it runs, it kills all my ssh connections and whatever else is open at that time.

---

### Post by cntrtrst on 2008-10-28
wrong.  It's actually thunderbird causing this, which I've confirmed by the fact that when I don't run it the problem goes away. Still don't now why.

---

### Post by cntrtrst on 2008-11-01
ok that's not it either.  don't know what on earth it is.

---

