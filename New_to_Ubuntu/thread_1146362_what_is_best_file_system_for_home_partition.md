---
title: "what is best file system for home partition?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-02
Hi
I know that there are several file systems for linux, I am wondering which one is the best option for home partition, should I go with EXT3, EXT4 or raiserFS or maybe something else?

Thanks.

---

### Post by y_garti on 2009-05-02
i use ext4 on my home pc and it works fine (you even Notice the speed improvement)
but you need to rember that is still a new file system and some users report problems with this file system (for me it works great)

---

### Post by HavocXphere on 2009-05-02
I'd go with ext4...but be sure to always have up-to-date backups, cause there are reports of ext4 resulting in data loss.

---

### Post by y_garti on 2009-05-02
they had a bug in the rc 9.04 that when you working with a big file (10 gb+) some time you got a corporation in your file system but they fix it in the final version

but still its very important to back up your system

---

### Post by RyanVanDiemen on 2009-05-02
if you're not sure you'd better stick with ext3. Ext4 works well for me but if you're not sure don't risk it (yet).reiser - i know suse used this in my pre-ubuntu age (they might still do). I personally didn't see any difference between ext3 and reiser.

---

### Post by PhrankDaChickenGeek on 2009-05-02
I stuck with ext3 for my home partition, and put ext4 on my root partiton. That way, I can downgrade if need be as well.
(Which I might - This Intel Graphics driver thingy isn't working too well right now...)

---

### Post by swoody on 2009-05-02
As the others have said, I'd use ext4 personally. I like the extra little bit of performance, and I keep backups of any important data, so I'm not worried about the few cases where people have lost data. I've never had any issues with data loss, fyi. If you're still a little nervous about that, ext3 is really nice, and will be compatible across many distros as well as if you reinstall an older version of Ubuntu. It's mostly a personal preference, there really is no *best* choice here, but just what may be better for you :)

---

