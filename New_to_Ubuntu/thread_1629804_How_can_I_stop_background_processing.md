---
title: "How can I stop background processing?"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by MHC on 2010-11-24
I am running Ubuntu 10.04 and seem to have a copying process running in the background that has gone wrong. I have closed the terminal, but it is still trying to copy apparently, as I cannot dismount my external hard drive because of it. How can I stop it?

---

### Post by bioterror on 2010-11-24
> **MHC said:**
> I am running Ubuntu 10.04 and seem to have a copying process running in the background that has gone wrong. I have closed the terminal, but it is still trying to copy apparently, as I cannot dismount my external hard drive because of it. How can I stop it?

With ps check which pid is it using and with kill, you kill that process.

```
ps aux |more
kill -9 <pid>
```

---

### Post by MHC on 2010-11-24
Great, that fixed it:) Thanks.

---

