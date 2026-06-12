---
title: "dmesg skype"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-30
I have just taken a look at dmesg |tail and see the following

process `skype' is using obsolete setsockopt SO_BSDCOMPAT

What does this mean and should it be fixed?

---

### Post by alphacrucis2 on 2010-05-30
> **expatCM said:**
> I have just taken a look at dmesg |tail and see the following

process `skype' is using obsolete setsockopt SO_BSDCOMPAT

What does this mean and should it be fixed?

I am getting that too. Doesn't seem to be causing any obvious problem. A search showed up the same message in older versions of Skype a couple of years ago. Haven't found anything definitive.

Edit: Have found a claim that the message is harmless though no explanation was given.

---

### Post by expatCM on 2010-05-30
Yes, I noticed that Fedora users were having fun with this some years ago and then the problem suddenly went away.  

I did not manage to find any threads that were saying what the message means and whether or not it really is a problem.  Some seem to blame it on problems with skype video but I get the impression that this was a diversion rather than a problem.

Since this has only recently appeared I wonder if it is related to the new kernel update ...  but since I do not understand the message I should not speculate ..

---

