---
title: "nfs strange behavior"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by etienne.navarro on 2007-01-12
I have a strange problem with some nfs mounts.
Two computer, alice and bob

Bob shares, via nfs, **/mnt/share-bob** and can be mounted by Alice fine.
Alice shares, again via nfs, **/mnt/share-alice** and can be mounted by Bob fine.

Ok here is where the problem starts:
If Alice mounts the Bob share in Alice's shared directory
```
user@alice:~$ mount bob:/mnt/share-bob /mnt/share-alice/
```Then if Bob mounts the Alice share to some temporary directory
```
user@bob:~$ mount alice:/mnt/share-alice /mnt/tmp
```On Bob when going to /mnt/tmp, its empty. It should have the contents of share-alice in it which has the contents of share-bob in it. So should be showing the contents of share-bob.

I know this seems like a dumb thing to do, but I've simplified the problem for clarity.

Anyone know why this is happening?

---

### Post by PurplePenguin on 2007-01-12
Hey, enough talk about Alice mounting Bob!  This is a family forum! :P

As far as I can see in your example, you're mounting alice:/share-alice which doesn't exist... should be alice:/**mnt/**share-alice, right?  Since you're trying to share a directory that doesn't exist, it'll come up empty.

---

### Post by etienne.navarro on 2007-01-12
Whoops, made a typo, should be
```
user@bob:~$ mount alice:/mnt/share-alice /mnt/tmp
```

---

