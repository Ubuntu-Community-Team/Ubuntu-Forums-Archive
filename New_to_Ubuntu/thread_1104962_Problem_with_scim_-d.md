---
title: "Problem with scim -d"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by luckymancvp on 2009-03-24
I run command "scim -d" so it allays is defaul input method. 
I want to some program run with scim. How to do it.
Because, something my Opera Internet can't type a letter. I must minimize it first, then type letter.

---

### Post by fly-by-night on 2009-03-24
SCIM with Opera on Ubuntu
[http://cworld.wikidot.com/adm:setup-scim-for-opera](http://cworld.wikidot.com/adm:setup-scim-for-opera)

edit
[http://dergrosseverraeter.wordpress.com/category/opera/](http://dergrosseverraeter.wordpress.com/category/opera/)

---

### Post by luckymancvp on 2009-03-25
Thanks you, But it doesn't solve problem "scim -d".

---

### Post by CRCarl on 2009-03-25
You need to install an application so Opera can use scim.

```
sudo aptitude install scim-bridge-client-qt
```

After that you need to logout and log back in, then start scim.

```
scim -d
```

That should do it.

---

### Post by luckymancvp on 2009-03-25
thanks, my opera run well

---

