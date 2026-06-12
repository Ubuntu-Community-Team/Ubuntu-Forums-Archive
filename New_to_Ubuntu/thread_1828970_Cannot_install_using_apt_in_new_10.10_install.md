---
title: "Cannot install using apt in new 10.10 install"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by redfox1160 on 2011-08-19
I just installed 10.10 on my machine, but I cannot download anything with apt. I tried running
```
sudo apt-get install vim
```
but it returned
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'vim' has no installation candidate

```

Does anyone know why this is happening? Do I have to enable apt? I don't remember doing this in 10.04. Thanks!

---

### Post by lmarmisa on 2011-08-20
Do you get the same problem using Synaptic?. Open Synaptic and take a look to Settings -> Repositories. If you cannot download packages, you could try to change the download server ( Download from: ), Close and finally click on Reload.

---

