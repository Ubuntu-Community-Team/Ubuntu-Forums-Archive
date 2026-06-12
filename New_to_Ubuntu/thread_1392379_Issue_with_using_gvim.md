---
title: "Issue with using gvim"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by sm_here on 2010-01-28
When opening a file using gvim, i get the message:
** (gvim:15881): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed

How can this be rectified?

---

### Post by sisco311 on 2010-01-28
It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188)

Use [this]("https://launchpad.net/~jk-ozlabs/+archive/vim") PPA repository to install vim.

```
sudo add-apt-repository ppa:jk-ozlabs/vim
sudo apt-get update
sudo apt-get install vim
```

---

### Post by sm_here on 2010-01-28
> **sisco311 said:**
> It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188)

Use [this]("https://launchpad.net/~jk-ozlabs/+archive/vim") PPA repository to install vim.

```
sudo add-apt-repository ppa:jk-ozlabs/vim
sudo apt-get update
sudo apt-get install vim
```
Thanks again. It's working fine now

---

