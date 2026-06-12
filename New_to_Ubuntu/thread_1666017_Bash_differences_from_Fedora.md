---
title: "Bash differences from Fedora"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by bill.damage on 2011-01-13
Hi,

On Fedora 12 I use bash scripts simplified to this:

#!/bin/sh
for name in "one" "two" "three"
do
 if [[ $name == t* ]]
 then
   echo $name
 fi
done

Which give the expected output
two
three

On my ubuntu box this gives
dev.sh: 10: [[: not found
dev.sh: 10: [[: not found
dev.sh: 10: [[: not found

Is there something I need to do to activate a bash feature to make them compatible please?

Thanks

---

### Post by solar george on 2011-01-13
I what you are using there (IIRC) is a bashism, if on fedora bash is the default /bin/sh it will run fine, however on ubuntu dash (which is rather more limited) is linked to /bin/sh. If you use /bin/bash instead of /bin/sh it should work on both systems.

---

### Post by TeoBigusGeekus on 2011-01-13
> **solar george said:**
> If you use /bin/bash instead of /bin/sh it should work on both systems.
In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.
See attached screenshot (from arch)

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

`--> ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

`--> ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

`--> ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by sisco311 on 2011-01-13
> **TeoBigusGeekus said:**
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.
See attached screenshot (from arch)

In Ubuntu, /bin/sh is a symlink to dash ([**D**ebian **A**lmquist **sh**ell]("http://en.wikipedia.org/wiki/Debian_Almquist_shell")).

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

`--> ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by solar george on 2011-01-13
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.

But not on ubuntu (and debian) which use dash because it is smaller and less resource intensive and therefore better for use in unattended scripts (ones that need bashisms can use /bin/bash or reconfigure the symlinks).
If you don't believe me try the following on a recent ubuntu (or debian) install;
```

`--> ls -l `which sh`
lrwxrwxrwx 1 root root 4 2011-01-10 19:33 /bin/sh -> dash

```

---

### Post by sisco311 on 2011-01-13
> **TeoBigusGeekus said:**
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.
See attached screenshot (from arch)

In Ubuntu, /bin/sh is a symlink to dash ([**D**ebian **A**lmquist **sh**ell]("http://en.wikipedia.org/wiki/Debian_Almquist_shell")).

---

### Post by sisco311 on 2011-01-13
> **TeoBigusGeekus said:**
> In almost all modern linux distros (ubuntu and fedora included I think), sh is just a symbolic link to bash; therefore /bin/bash and /bin/sh are the same thing.
See attached screenshot (from arch)

In Ubuntu, /bin/sh is a symlink to dash ([**D**ebian **A**lmquist **sh**ell]("http://en.wikipedia.org/wiki/Debian_Almquist_shell")).

---

### Post by solar george on 2011-01-13
Seems the forums are having a bad day for duplicating posts, this is the second thread I've seen it in today.

---

### Post by TeoBigusGeekus on 2011-01-13
Didn't know about dash, sorry everyone...

By the way, is there an echo in here? :lolflag:

---

