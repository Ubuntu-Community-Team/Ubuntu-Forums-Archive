---
title: "Problem encounter on running chattr"
date: 2018-04-29
forum: Networking &amp; Wireless
---

### Post by satimis on 2018-04-29
Hi all,

Ubuntu 18.04 desktop

I need to keep /etc/resolv.conf unchanged on reboot and ran following command on terminal:-

# chattr +i /etc/resolv.conf
```

Usage: chattr [-pRVf] [-+=aAcCdDeijPsStTu] [-v version] files...

```

$ chattr manual```

Must use '-V', =, - or +

```
Please help how to fix this problem?  Thanks

Regards
satimis

---

### Post by jeremy31 on 2018-04-29
I don't think that file is allowed to be set immutable, try adding any changes you want to /etc/resolvconf/resolv.conf.d/head

---

### Post by satimis on 2018-04-29
> **jeremy31 said:**
> I don't think that file is allowed to be set immutable, try adding any changes you want to /etc/resolvconf/resolv.conf.d/head
Hi,

Thanks for your advice.

$ cat /etc/resolvconf/resolv.conf.d/head```

cat: /etc/resolvconf/resolv.conf.d/head: No such file or directory

```

Whether I need to create this file?

Regards
satimis

---

### Post by jeremy31 on 2018-04-29
What changes are you trying to make?
I can't be sure that resolvconf is used in 18.04

---

### Post by SeijiSensei on 2018-04-29
I suspect you can't make resolv.conf immutable because it's now a symlink.

---

### Post by satimis on 2018-04-29
> **jeremy31 said:**
> What changes are you trying to make?
I can't be sure that resolvconf is used in 18.04
on /etc/resolv.conf

comment out;
nameserver 127.0.0.53
(It can't resolve domain)

and add my nameserver there.

It works after making such changes and restarting networking running'
```

$ sudo service-manager restart

```

But after reboot all changes gone.

satimiks

---

### Post by satimis on 2018-04-29
> **SeijiSensei said:**
> I suspect you can't make resolv.conf immutable because it's now a symlink.
ls -al /etc/resolv.conf
```

lrwxrwxrwx 1 root root 39 Apr 29 18:16 /etc/resolv.conf -> ../run/systemd/resolve/stud-resolv.conf

```

Edit
===
$ locate stud-resolv.conf
No output

---

### Post by jeremy31 on 2018-04-29
*Thread moved to **Networking & Wireless**.*

---

