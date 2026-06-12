---
title: "failure cleaning /tmp"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by phil66 on 2009-08-02
Ubuntu Hardy

During boot I get a message saying "bootclean..failure cleaning /tmp"
There are many files in /tmp

Do I need to correct this and if so how??

---

### Post by Soul-Sing on 2009-08-02
After every reboot Ubuntu should clean your temp direct.
You could clean/empty this direct.
```
gksudo nautilus
```
==>empty the content of the temp direct. after navigating to this direct.
Close nautilus. Reboot again.

---

### Post by llamabr on 2009-08-02
[http://ubuntuforums.org/showthread.php?t=754359](http://ubuntuforums.org/showthread.php?t=754359)

first hit on google

---

### Post by Primefalcon on 2009-08-02
well temp empties each reboot, and I highly recommend against cleaning it during running as you could get unwanted side effects, but I suppose a command

```
sudo rm -Rf /tmp/*
```

would do what your wanting, but I still advise highly against it

---

### Post by phil66 on 2009-08-02
> **Primefalcon said:**
> well temp empties each reboot, and I highly recommend against cleaning it during running as you could get unwanted side effects, but I suppose a command

```
sudo rm -Rf /tmp/*
```

would do what your wanting, but I still advise highly against it

It does not empty after each boot.

Is there a way to correct what ever is not allowing it to empty /tmp on each boot?

---

