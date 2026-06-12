---
title: "updates won't install"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ajn132 on 2009-07-08
When I try to install new updates from the update manager i get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Considering I am an extreme novice with ubuntu i have no idea what to do. let me know if more information is needed to solve this.

---

### Post by mano cazalet on 2009-07-08
and what happens if you run

[HTML]sudo dpkg --configure -a[/HTML]

in terminal

---

### Post by ajn132 on 2009-07-08
I get:

[html]dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
 newline in field name `
[/html]

---

### Post by wojox on 2009-07-08
Remove damaged files:

```
cd /var/lib/dpkg/updates rm *
```

---

### Post by ajn132 on 2009-07-08
> **wojox said:**
> Remove damaged files:

```
cd /var/lib/dpkg/updates rm *
```

i put that in and it didn't seem to do anything, and the updates still don't work. :(

---

### Post by wojox on 2009-07-08
Now do:

```
sudo apt-get update
```

Then

```
sudo apt-get upgrade
```

---

### Post by ajn132 on 2009-07-08
still getting
[html]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 [/html]

---

### Post by wojox on 2009-07-09
dpkg --configure -a

What else does it show when you run that?

---

### Post by mano cazalet on 2009-07-09
after removing the updates with cd /var/lib/dpkg/updates rm *
whats the output of 

sudo dpkg --configure -a
?

---

### Post by ajn132 on 2009-07-09
[HTML]cd /var/lib/dpkg/updates rm *[/HTML]

---

### Post by tarps87 on 2009-07-09
> **ajn132 said:**
> [HTML]cd /var/lib/dpkg/updates rm *[/HTML]

The above command will do nothing without super user permissions

```
sudo rm /var/lib/dpkg/updates/0002
```

---

