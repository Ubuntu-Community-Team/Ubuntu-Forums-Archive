---
title: "How to Hibernate...?"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Its_Rishi on 2011-02-20
I can't find how to hibernate ubuntu anywhere at options...
i need an option at shut down button at top right at the screen...

---

### Post by cariboo on 2011-02-20
There are problems with swap partition corrutption with some kernels. If you swap is corrupted the hibernate option won't show up in the menu. You can test this by disabling swap and turning it back back on again. The first thing to do is to make sure the uuid for swap is the same as in /etc/fstab:

```
sudo blkid
```

the result should look something like this:

```
/dev/sdb2: UUID="0ff3075d-8424-4194-a503-bf97cc228f79" TYPE="swap"
```

compare your result with the value in /etc/fstab, if they match you are ok, if not copy and paste the value you got from the blkid command into /etc/fstab. Then turn swap off:

```
sudo swapoff -a
```

and back on again:

```
sudo swapon -a
```

Reboot, and the hibernate option should be back in the On/Off menu.

Now hibernate your system for a couple of minutes, then  wake it up again. Check the uuid of the swap partition to see if it has changed, if it has, you'll have to install hibernate from the repositories in order to have hibernate work reliably for you

**Note** The devs have disabled the hibernate option in Natty.

---

