---
title: "fstab space in line"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by rmmsteve on 2011-06-30
I'm trying to mount this afp connection in fstab but I keep getting an error.

afpfs#afp://[user]:[pass]@[address]/**Shared Items**/ /var/www/Share/ fuse user=www-data,group-fuse 0 0

I've tried with no success
afpfs#afp://[user]:[pass]@[address]/Shared\040Items/ /var/www/Share/ fuse user=www-data,group-fuse 0 0

---

### Post by jtarin on 2011-06-30
Look a little closer at the [documentation]("https://help.ubuntu.com/community/Fstab") and you will see why.

---

### Post by kamaji792 on 2011-07-01
Hi @rmmsteve,

Try escaping the space with '\ '.

e.g.
```
afpfs#afp://[user]:[pass]@[address]/Shared\ Items/ /var/www/Share/ fuse user=www-data,group-fuse 0 0
```

atb K

---

### Post by compmodder26 on 2011-07-01
"#" represents a comment in fstab

So everything after that comment is disregarded

Basically, the only thing that ubuntu sees as an actual item to parse is "afpfs"

Try this:
```
# afpfs
afp://[user]:[pass]@[address]/Shared\ Items/ /var/www/Share/ fuse user=www-data,group-fuse 0 0
```

Edit: And I'm pretty sure at the end of the line you want "group=fuse" and not "group-fuse"

---

### Post by jtarin on 2011-07-01
[http://blogs.oracle.com/lowbit/entry/easy_afp_autmount_on_os](http://blogs.oracle.com/lowbit/entry/easy_afp_autmount_on_os)

---

