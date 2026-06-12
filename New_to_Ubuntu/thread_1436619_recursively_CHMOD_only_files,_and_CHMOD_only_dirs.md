---
title: "recursively CHMOD only files, and CHMOD only dirs"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Hailwood on 2010-03-22
Hi guys

I know you can loop recursively by doing eg 
sudo CHMOD 644 -R /var/www

but that will chmod both files and directories?

is there a way to chmod just file or just dirs?

possibly a flag?

---

### Post by undecim on 2010-03-22
you can use find.

to do only files:
```
find -type f -exec chmod 644 {} ;
```

for directories:
```
find -type d -exec chmod 644 {} ;
```

---

### Post by asmoore82 on 2010-03-22
You gain a slight boost in efficiency by using `find` in combination with `xargs`
```
find */some/dir* -type **f** -print0 | xargs -0 chmod 644
```
```
find */some/dir* -type **d** -print0 | xargs -0 chmod 755
```

The catch is if you need `sudo` you must `sudo` both sides:
```
**sudo** find /var/www -type f -print0 | **sudo** xargs -0 chmod 644
```

---

