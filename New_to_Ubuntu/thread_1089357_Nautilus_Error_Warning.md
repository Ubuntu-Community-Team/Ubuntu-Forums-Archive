---
title: "Nautilus Error Warning"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-07
** (nautilus:15951): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/joan is not a well formed usershare file.
info_fn: Error was Path is not a directory.


Can somebody please explain what all this means.

---

### Post by Xiong Chiamiov on 2009-03-07
It looks like something's wrong with your samba configuration.  What did you do to cause this?  Is it reproducable?

---

### Post by dunbrokin on 2009-03-07
> **Xiong Chiamiov said:**
> It looks like something's wrong with your samba configuration.  What did you do to cause this?  Is it reproducable?

No idea....it comes up on my Nautilus terminal when I close down Nautilus.

---

### Post by iamkrazee on 2009-03-07
do you run it normally or as super user?

---

### Post by dunbrokin on 2009-03-07
> **iamkrazee said:**
> do you run it normally or as super user?

No, normally just "sudo nautilus"...but it does not seem to make any difference.

---

### Post by Dan_Dranath999 on 2009-03-07
It happens to me too (only with Hardy), but until today no big deal...

(But don't try to ***Sudo Nautilus*** if you have an empty disc in the cdrom tray, it just won't launch. Remove the blank disc from the drive, and everything goes back to normal. weird bug)

---

### Post by t0p on 2009-03-07
My tuppence worth: the "preferred" way to run nautilus as superuser is to hit Alt+F2, then type in the box:

```
gksudo nautilus
```

I have no idea what the precise difference between *sudo* and *gksudo* might be.  All I know is that *gksudo* is the command you "should" use when you want to run a gui program as superuser.

Dunbrokin: when you run **sudo nautilus**, you are running it as superuser.  That's what the use of **sudo** (and **gksudo**) does.

---

### Post by dunbrokin on 2009-03-07
Sorry, but none of those last two suggestions worked: i.e. gksudo or not having a cd in the cd drive.

---

