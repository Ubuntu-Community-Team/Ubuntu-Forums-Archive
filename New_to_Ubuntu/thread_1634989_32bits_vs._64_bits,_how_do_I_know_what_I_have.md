---
title: "32bits vs. 64 bits, how do I know what I have?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by BCMerlin on 2010-12-01
I see it's handy to know which one is on my laptop, 32bit or 64bit, but I actually have no clue. Where and how can I check this?

My OS is Ubuntu 10.10

---

### Post by CharlesA on 2010-12-01
Run this:

```
uname -a
```

If it says i686 or i386, you are running the 32-bit version.
If it says x86_64, you are running the 64-bit version.

---

### Post by BCMerlin on 2010-12-01
Aha so I run a 32-bit version.
```
Linux barbara-Aspire-5715Z 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```

Why is it important to know this? I mean, in which way can I apply this knowledge?

---

### Post by philinux on 2010-12-01
> **BCMerlin said:**
> Aha so I run a 32-bit version.
```
Linux barbara-Aspire-5715Z 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```

Why is it important to know this? I mean, in which way can I apply this knowledge?

If you have a 64 bit machine and say 4 gig of ram the I would run the 64 bit version. 

I have a 64 bit laptop with only 2 gig of ram but still installed the 64 bit version.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by CharlesA on 2010-12-01
> **BCMerlin said:**
> Aha so I run a 32-bit version.
```
Linux barbara-Aspire-5715Z 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```

Why is it important to know this? I mean, in which way can I apply this knowledge?

That's the 32-bit version.

You don't really need to know what architecture you are running for day-to-day tasks. If you stick to the repos, you should be fine, as they'll install whatever version of the software that is correct for your machine (32-bit or 64-bit).

It gets a little messy if you are installing third-party stuff tho, if that was the case, you might need to know if you were running 32-bit or 64-bit.

---

### Post by BCMerlin on 2010-12-01
Ok, thanx. O:)

---

### Post by CharlesA on 2010-12-01
Don't forget to mark the thread as solved from thread tools. :)

---

