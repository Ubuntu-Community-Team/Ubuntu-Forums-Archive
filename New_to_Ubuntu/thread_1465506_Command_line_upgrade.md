---
title: "Command line upgrade"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by da burger on 2010-04-29
Is there a terminal command I can use to upgrade from 9.10 to 10.04? I always prefer to use the terminal to do the larger things. Thanks

---

### Post by arrrghhh on 2010-04-29
> **da burger said:**
> Is there a terminal command I can use to upgrade from 9.10 to 10.04? I always prefer to use the terminal to do the larger things. Thanks

```
sudo do-release-upgrade
```

There is a way to do a dist-upgrade with apt-get and aptitude, I've just been told this is "the way" you're *supposed* to do it.

Well, unless you're doing update-manager -d, which would involve a GUI so I didn't mention it :D

---

### Post by bodhi.zazen on 2010-04-29
For anyone else looking at this thread see:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by arrrghhh on 2010-04-29
> **bodhi.zazen said:**
> For anyone else looking at this thread see:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Thanks, that's an excellent reference guide :D

---

