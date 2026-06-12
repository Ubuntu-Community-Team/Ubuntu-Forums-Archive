---
title: "Problem with symlinks"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-12-24
I am trying to link my /home/username/Videos to my /Windows/User/name/Video.
I tried to ```
ln -s Videos /Windows/Users/Jason/Videos

```but when I ls -la it doesn't show up ```
...
drwx------  2 jason jason  4096 2009-10-31 07:58 .update-notifier
drwxr-xr-x  2 jason jason  4096 2009-12-24 09:21 Videos
drwxr-xr-x  4 jason jason  4096 2009-11-30 13:24 .VirtualBox
...
```

---

### Post by coffeecat on 2009-12-24
Where is /Windows/Users/Jason/Videos? Is that in a Windows partition? Because /Windows is an unusual folder to have in the root of your filesystem.

Is /Windows the mountpoint for your Windows C: partition? Or something else?

---

### Post by the_midnighter on 2009-12-24
Assuming you have a /Windows directory from root:

Two things:

1) You need to use
```
ln -s  /Windows/User/name/Video Video
```

2) The Video directory shouldn't exist.

---

### Post by sandyd on 2009-12-24
> **slughappy1 said:**
> I am trying to link my /home/username/Videos to my /Windows/User/name/Video.
I tried to ```
ln -s Videos /Windows/Users/Jason/Videos

```but when I ls -la it doesn't show up ```
...
drwx------  2 jason jason  4096 2009-10-31 07:58 .update-notifier
drwxr-xr-x  2 jason jason  4096 2009-12-24 09:21 Videos
drwxr-xr-x  4 jason jason  4096 2009-11-30 13:24 .VirtualBox
...
```
your doing it backwards
should be
```
ln -s /Windows/Users/Jason/Videos ./Videos
```

---

### Post by slughappy1 on 2009-12-24
I have my Windows 7 auto mount, using fstab, to /Windows on boot. Oops, I didn't realize I had it backwards. Are you sure that you meant to put it ./Video? Shouldn't it be just Video?

---

### Post by SuperSonic4 on 2009-12-24
> **slughappy1 said:**
> I have my Windows 7 auto mount, using fstab, to /Windows on boot. Oops, I didn't realize I had it backwards. Are you sure that you meant to put it ./Video? Shouldn't it be just Video?

They're one and the same: "." means "current directory" but leaving it out implies "current directory"

---

