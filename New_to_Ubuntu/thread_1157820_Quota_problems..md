---
title: "Quota problems."
date: 2009-05-13
forum: New to Ubuntu
---

### Post by etali on 2009-05-13
I can't install anything at the moment, because I keep getting disk quota exceeded errors.

I've got plenty of space left (only 20% disk space used), so I'd like to either turn off quotas, or change them.

If I try quotaoff -a, I get this error:

quotaoff: quotactl on /dev/simfs [/]: Invalid argument
quotaoff: quotactl on /dev/simfs [/]: Invalid argument

edquota shows everything except blocks and inodes is set to zero, and it won't let me change those.

Any advice much appreciated.

---

### Post by skymera on 2009-05-13
Did you set the quotas yourself?

what filesystem do you use?

---

### Post by etali on 2009-05-13
Thanks for your response.

This is a VPS, I didn't set it up (so didn't set the quotas).  Actually, this is the first time I've ran an Ubuntu server so the whole thing is a bit of a learning experience.

How would I check what file system it's running?

---

