---
title: "The way linux handles ram confuses me"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by sunrex on 2010-03-04
Don't get me wrong, I understand why it stores it in cache. But its really downright irritating when it says you have 144MB free ram left, then you backup user data (so lots of HDD transfer usage, RAM usage and CPU usage) and after its done backing up it says 7.4GB free....

Seriously, WHY was it designed this way?. I don't just mean the cache.

Also, why the heck would top say 144MB free when the rest is mostly in cache?.

Bah.

Linux ram management = utter confusion...

---

### Post by hansdown on 2010-03-04
Hi sunrex.

It's said to be faster this way.

Here's some info.

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

---

### Post by 3rdalbum on 2010-03-04
> **sunrex said:**
> Don't get me wrong, I understand why it stores it in cache. But its really downright irritating when it says you have 144MB free ram left, then you backup user data (so lots of HDD transfer usage, RAM usage and CPU usage) and after its done backing up it says 7.4GB free....

Seriously, WHY was it designed this way?. I don't just mean the cache.

Also, why the heck would top say 144MB free when the rest is mostly in cache?.

Bah.

Linux ram management = utter confusion...

It depends what program you're asking. Gnome System Monitor gives you the figure without cache. Free tells you the total used RAM, and how much of that is cache.

I'll answer your first question, it's quite easy. The data that's cached before your backup operation is data that is only destined to be transferred between your main disk and operating system/programs. When you start copying to another disk, that data gets flushed from cache to make way for the copy cache. When you've finished backing up and you unmount the destination disk, then the cached data is deemed to be unnecessary because the destination is gone, so it's flushed, leaving you with very little cache in use.

---

