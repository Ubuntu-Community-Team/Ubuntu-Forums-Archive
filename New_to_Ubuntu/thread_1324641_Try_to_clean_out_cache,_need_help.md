---
title: "Try to clean out cache, need help"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by berri67 on 2009-11-12
I have ubuntu version 8.04 LTD.

I tried to clean out the cache using the command:

  sudo apt-get autoclean && sudo apt-get clean

I got the following back:

E:  could not get lock /var/lib/dpkg/lock-open (11 resource temporarily unavailable)

E:  unable to lock the administration directory (/var/lib/dpkg/) is another process using it?

I don't know what the above means.  Please help.

Also, I did an update previously, and would like to know how to restore to an earlier time.  Someone said to go to a third kernal, but I don't know what they meant.  

Any help would be appreciated.
Thanks.

---

### Post by coldReactive on 2009-11-12
What kind of cache?

DNS Cache?
```
sudo apt-get install nscd
service nscd restart
```

Firefox Cache?
Tools > Clear recent history

---

### Post by egalvan on 2009-11-12
The errors mean that there is another process that is using the files/directories needed by the command you are running

make sure that there are no other instances of apt-get, aptitude or Synaptic running.

When I have this problem, and I can't find other processes, I break down and re-boot.

Yes, there are ways to avoid the re-boot, but I am lazy. :)

---

### Post by jmszr on 2009-11-12
berri67,

This may help:

```
sudo rm /var/cache/apt/*.bin
```

It may not be applicable, but worth a try.

---

### Post by wojox on 2009-11-12
> **egalvan said:**
> the errors mean that there is another process that is using the files/directories needed by the command you are running

make sure that there are no other instances of apt-get, aptitude or synaptic running.

When i have this problem, and i can't find other processes, i break down and re-boot.

Yes, there are ways to avoid the re-boot, but i am lazy. :)

+1

---

