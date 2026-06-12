---
title: "odt is locked for editing"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-12
Hi,

Im accessing an odt file in one Ubuntu os on one disc by another edition of Ubuntu on another disc. Permissions recognizes me as the owner, but won't let me write to it. It is "Locked for editing"

/9.10/media/2nd HDD 9.10 /home/nnjond.../X.odt

Is there a bash command or something that will solves this?

Thanks

---

### Post by LowSky on 2010-04-12
> **nnjond said:**
> Hi,

Im accessing an odt file in one Ubuntu os on one disc by another edition of Ubuntu on another disc. Permissions recognizes me as the owner, but won't let me write to it. It is "Locked for editing"

/9.10/media/2nd HDD 9.10 /home/nnjond.../X.odt

Is there a bash command or something that will solves this?

Thanks

Yes, just because you have the same user name, doesn't mean you have access to the file.

copy the file locally, like the desktop. this way the original is fine just in case

```
sudo chmod 777 *filename*
```

---

