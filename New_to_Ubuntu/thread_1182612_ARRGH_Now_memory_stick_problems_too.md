---
title: "ARRGH Now memory stick problems too"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by John Hale on 2009-06-09
I'm having a couple of issues at the moment, I have 2 users on my pc with accounts in both windows and ubuntu, and have problems with stuff like viewing and writing to the windows drive worked fine until yesterday, and now I get "cannot mount volume" and underneath something like I'm not privileged to. Now I get that on my memory stick to which I've always backed stuff up to I generally work in ubuntu backup to the stick and print in windows, for a while I've had cards from a camera in a card reader that sometimes will view and sometimes can't see the card at all probably doing something wrong

Please help

---

### Post by dileepm on 2009-06-09
If you are a root user you should be able to mount the volumes. Might be security permissions you have set. Automounting/hot plug the volumes might solve the problem.

---

### Post by John Hale on 2009-06-09
How do I check if I'm a root user? And How do I make this hot plugging permanent so I don't have this issue in the future please?

---

### Post by Saghaulor on 2009-06-09
You can try to do the following:

```
sudo nautilus
```

That will run Nautilus in a privileged state, which should allow it to mount the partitions, that is, assuming they're not damaged.

Also, read up on the mount command.

```
man mount
```

Because you can run that as sudo, which would be much more preferable security wise than to run Nautilus as sudo.

---

