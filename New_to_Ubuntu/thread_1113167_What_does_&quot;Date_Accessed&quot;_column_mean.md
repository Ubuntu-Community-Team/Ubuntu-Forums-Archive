---
title: "What does &quot;Date Accessed&quot; column mean?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by ami_nakata on 2009-04-01
A great many files that I haven't accessed myself anytime recently show a "date accessed" that's today's date. Many of them even show they were accessed at the exact same second.

I thought that this column refered to the last date **I** accessed the a given file, but that's evidently not so.  Is what I'm seeing in this column the result of some cron-executed system daemon, like the indexing process "updatedb" or something, accessing the files? 

thanks, 

- ami

---

### Post by steeleyuk on 2009-04-01
I think Tracker, if its running, modifies the access time.

Anyway, the accessed time should be the time you access the file, most of mine are correct but I don't run Tracker.

---

### Post by philinux on 2009-04-01
> **ami_nakata said:**
> A great many files that I haven't accessed myself anytime recently show a "date accessed" that's today's date. Many of them even show they were accessed at the exact same second.

I thought that this column refered to the last date **I** accessed the a given file, but that's evidently not so.  Is what I'm seeing in this column the result of some cron-executed system daemon, like the indexing process "updatedb" or something, accessing the files? 

thanks, 

- ami

The date modified column is the important one.

---

