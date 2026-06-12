---
title: "Does EXT4 still have file corruption issues?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by CharlesA on 2010-04-29
I am thinking about moving my RAID array up to EXT4 instead of EXT3 due to a few of the benefits, but I don't want to risk file corruption.

I seem to recall that some time ago EXT4 had problems with files over a certain size, is that still a problem?

---

### Post by Hospadar on 2010-04-29
I've never had any problems after a year or two on several computers.  Benchmarks show it to be faster and it has some new journal features which should make it more reliable, so i'd go ahead and use it.

---

### Post by florus on 2010-04-29
I Have been on ext4 since the start of Karmic and have found it totally reliable and much faster than ext3.
Do  a fresh install and format the partitions to ext4. There have been problems with converting an existing setup, I believe.

---

### Post by CharlesA on 2010-04-29
Thanks!

I did a bit of reading earlier that said that the "problem" (file corruption if there was loss of power) was fixed with kernel 2.6.30 (I think).

Not that my server has any problems with unsafe shutdowns or power outages, I've been sticking with EXT3 "just in case."

---

### Post by CharlesA on 2010-04-29
Wow double post. >.<

---

### Post by lovinglinux on 2010-04-29
> **florus said:**
> I Have been on ext4 since the start of Karmic and have found it totally reliable and much faster than ext3.

+1

I have experienced several power outages and never lost anything. I don't know about the file sizes tho.

---

