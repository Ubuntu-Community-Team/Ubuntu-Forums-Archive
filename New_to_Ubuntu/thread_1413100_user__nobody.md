---
title: "user  nobody"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by burmese.numbnuts on 2010-02-22
I accidentally deleted the Ubuntu's default user "nobody". I was reading online posting and found out it had its own usage. How do I recover it?  :confused:

Thank you!

---

### Post by Barriehie on 2010-02-22
There's a thread for that! [http://ubuntuforums.org/showthread.php?t=1389080&highlight=recover+user](http://ubuntuforums.org/showthread.php?t=1389080&highlight=recover+user)

Edit: Just reread your post, this might not work... :(

---

### Post by gmargo on 2010-02-22
Here's the relevant info for user **nobody**.  You should be able to recreate it using **adduser**.

```

$ id nobody
uid=65534(nobody) gid=65534(nogroup) groups=65534(nogroup)

$ grep nobody /etc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh

$ grep nogroup /etc/group
nogroup:x:65534:

```

---

