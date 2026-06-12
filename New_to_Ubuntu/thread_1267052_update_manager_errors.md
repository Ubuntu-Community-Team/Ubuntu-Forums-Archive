---
title: "update manager errors"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by damo74 on 2009-09-15
I am using jaunty 9.04. while using the update manager, I keep getting the following error

Failed to fetch [http://www.e-oss.net/ubuntu/gutsy/./Packages](http://www.e-oss.net/ubuntu/gutsy/./Packages)  404 Not Found

Can anyone, in simple, easy to follow instructions advise how to resolve

---

### Post by sunchiqua on 2009-09-15
That's not an Ubuntu repository. How did you get it there ?


Remove it from your sources.list:```

gksudo gedit /etc/apt/sources.list
```Update database:
```
sudo apt-get update
```

---

### Post by wojox on 2009-09-15
Gutsy is EOL so like sun says get rid of it.

---

### Post by adalal on 2009-09-15
> **damo74 said:**
> I am using jaunty 9.04. while using the update manager, I keep getting the following error

Failed to fetch [http://www.e-oss.net/ubuntu/gutsy/./Packages](http://www.e-oss.net/ubuntu/gutsy/./Packages)  404 Not Found

Can anyone, in simple, easy to follow instructions advise how to resolve

Lol, well, that page really doesn't exist anymore, probably because it's for the old distro. Try removing it from the sources list like sunchiqua mentioned, or try updating that package listing to the latest distro you have. If you don't have the latest distro, I'd suggest you distro-upgrade:

```
sudo apt-get distro-upgrade 
```

---

### Post by damo74 on 2009-09-15
The link came from PYTRAINER.

Anyway I have now deleted from the sources list and the update manager seems to be working.

Thank you for your help.

---

