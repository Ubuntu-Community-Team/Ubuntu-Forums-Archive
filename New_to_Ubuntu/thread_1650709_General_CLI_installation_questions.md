---
title: "General CLI installation questions"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by beanco on 2010-12-22
How do you know the exact name of packages or rather, how do you find the exact name  when trying to install from CLI?

I am trying to install Geogebra and Google Earth and cannot figure out the exact names..

Yes, I will be able to find these with a little search work, but in general if you do not know the exact name, how can you find it easily?

I am sure there is a really simple answer, but I am having a brain fart at the moment....


Thanks

Robi

---

### Post by Elfy on 2010-12-22
You could look with apt-cache search 

```
apt-cache search *term* |more
```

---

### Post by nothingspecial on 2010-12-22
If you know part of the name, use the -n option.

For example

```
apt-cache search google | less
```

returns 162 packages. Where as

```
apt-cache search -n google | less 
```

returns 32 - narrows things down a little.

---

