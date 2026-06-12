---
title: "iMac G5 and fans."
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Lodbrok on 2010-12-15
Greetings.

The fans on my computer go full speed all the time.
The [wiki page on my iMac G5 Rev C]("https://wiki.ubuntu.com/iMacG5iSight?action=show&redirect=iMacG5revC") mentions that I should apply this ([http://bersace03.free.fr/pub/Linux/i...rm-pm121.patch]("http://bersace03.free.fr/pub/Linux/iMac%20G5/windfarm-pm121.patch")) patch to the latest Linux 2.6.24 source.

I skimmed the Internet for a bit, and still have no idea what to do.

Help, please?

EDIT: Running 10.10 and all updates are installed.

---

### Post by Lodbrok on 2010-12-15
Bump?

---

### Post by sandyd on 2010-12-15
that patch won't work with current versions of linux unless you install the 2.6.24 kernel manually.

post output of
```

uname -a
```

---

### Post by Lodbrok on 2010-12-15
```
patrick@Patrick:~$ uname -a
Linux Patrick 2.6.35-23-powerpc64-smp #41-Ubuntu SMP Fri Nov 26 04:21:34 UTC 2010 ppc64 GNU/Linux

```

---

### Post by Lodbrok on 2010-12-16
Bump?

---

### Post by sandyd on 2010-12-16
> **Lodbrok said:**
> ```
patrick@Patrick:~$ uname -a
Linux Patrick 2.6.35-23-powerpc64-smp #41-Ubuntu SMP Fri Nov 26 04:21:34 UTC 2010 ppc64 GNU/Linux

```
nope. kernels too new.
your going to have to find a newer patch.

---

