---
title: "ExpressVPN on Ubuntu 16.10"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by chaitan64arun on 2017-01-02
Hello All,

I had the exact problem as mentioned in this thread.
[https://ubuntuforums.org/showthread.php?t=2342534](https://ubuntuforums.org/showthread.php?t=2342534)

I could temporarily solve it by using *--ignore-depends*
Now I get a problem with ***'ERROR:BrokenCount>0***'

I can solve the error by 
```
sudo apt-get install -f
```

but it uninstalls expressvpn. Is there a proper way to install?

Any help is appreciated!

---

### Post by crander2 on 2017-01-03
Hi Chaitan64arun,

I get this error as well but just ignore it as it doesn't stop ExpressVpn from function properly.

Cheers

crander2

---

