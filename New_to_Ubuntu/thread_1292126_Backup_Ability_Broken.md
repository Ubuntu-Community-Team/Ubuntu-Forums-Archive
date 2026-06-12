---
title: "Backup Ability Broken???"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-10-15
I have tried 3 methods of backing up my /home. 

1- Deja Dup

2- Simple Backup

3- GRsync

NONE of them work. I get various error messages.

Please point me in the direction of using **dd** to copy (dump) my /home to a usb attached hard disk.

---

### Post by cariboo on 2009-10-15
The only method I'm familiar with is grsync, right now it seems to be broken in Karmic, so I just do it by hand, this is what I use.

```
rsync -av --delete /home/<me> <me>@server:restore 
```

In the above example /home/<me> is my home directory <me>@server:restore/ is the directory I store the backup on, on my server. You can use any target directory using the example.

---

### Post by mikix on 2009-10-27
I'm a developer of Deja Dup.  Sorry to hear it didn't work.  The version in Karmic (out in a couple days) might have fixed the bug you ran into, or you could try the official PPA [1].

Though if rsync works for you, that's good too.  :)

[1] [https://launchpad.net/~deja-dup-team/+archive/ppa](https://launchpad.net/~deja-dup-team/+archive/ppa)

---

