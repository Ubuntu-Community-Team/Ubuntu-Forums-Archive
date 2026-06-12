---
title: "Problem Installing nfs-common in Ubuntu 8.10"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by newtoubie on 2010-11-07
Hi.

I'm trying to install **nfs-common** in Ubuntu 8.10 standalone installation in order to set up an nfs client.  I have successfully installed **portmap** but when I try to install nfs-common I receive an error saying that **libevent1** is missing and the installation fails.  So I obtained a copy of libevent1 and tried to install that using the debian installer.  This fails too with the error "libevent already installed".

So it looks like there's a conflict here.  The installer finds libevent if you try to install it again but doesn't find it if you try to install something that depends on it.

Any ideas?

Thanks

---

### Post by cariboo on 2010-11-08
How are you trying to install nfs-common, if you type:

```
sudo apt-get install nfs-common
```

it will install the package and all the dependencies/recommends. You can also use the Software Center or Synaptic Package Manager.

---

### Post by sikander3786 on 2010-11-08
You are running 8.10? Support for 8.10 has ended. Are the repositories still working?

---

