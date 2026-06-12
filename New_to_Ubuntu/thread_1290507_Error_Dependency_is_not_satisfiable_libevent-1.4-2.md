---
title: "Error: Dependency is not satisfiable: libevent-1.4-2 (&gt;= 1.4.11-stable)"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by HitmanNumber86 on 2009-10-13
I'm running Ubuntu 9.04. I've run "apt-get upgrade." I've got Transmission 1.51. I'm trying to download Transmission 1.75. I keep getting the aforementioned error, upon attempting to install the package. Again...

Error: Dependency is not satisfiable: libevent-1.4-2 (>= 1.4.11-stable)

I've tried installing (with suggestion) libevent-dev, libevent-1.4-2, and libev-libevent-dev, with no luck.

From what I understand, the install package is dependant on the libevent package. Is this correct? Do I have to install the package manually?

Thanks, in advance.

---

### Post by swoody on 2009-10-13
You may also want to try installing libevent-core and libevent-extra. You can open a terminal, and run:
```
sudo apt-get install libevent-core-1.4-2 libevent-extra-1.4-2
```

Then give it another try. Let us know if this works or not :)

---

### Post by HitmanNumber86 on 2009-10-15
No success.

I couldn't download either  libevent-core, or libevent-extra.

---

### Post by HitmanNumber86 on 2009-10-18
C'mon guys. I'm new to Linux. If Linux can't run simple programs, I have to switch back to Windows. I hated Windows, and I don't want to go back.

---

### Post by mc4man on 2009-10-18
> If Linux can't run simple programs, .......
It appears you're trying to install a package built for karmic on jaunty.

While sometimes that can be done easily with no issues, other times it becomes more difficult or a poor idea.

In this case it's one of the latter two, you'd need to track the dependencies to see where that leads, and at this point that's not something I see you doing.

You could install karmic when it releases in a couple of wks. ( the Rc release is in a wk. I believe or find and add a jaunty ppa that has a newer transmission

Here's one for example
[https://launchpad.net/~bortis/+archive/ppa](https://launchpad.net/~bortis/+archive/ppa)

search page for ubuntu ppa's
[https://launchpad.net/ubuntu/+ppas?name_filter=transmission](https://launchpad.net/ubuntu/+ppas?name_filter=transmission)

If you don't know how to use a ppa then ask first, someone can square you up.

---

