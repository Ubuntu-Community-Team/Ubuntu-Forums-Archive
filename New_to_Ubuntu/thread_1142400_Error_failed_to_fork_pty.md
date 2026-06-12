---
title: "Error failed to fork pty"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by nspur on 2009-04-29
I get this error (Jaunty, just upgraded) from the package manager after clicking Install for a list of updates that it has found. Rebooting doesn't clear any error condition. What might be the problem? If it's on any importance, 5 of the reported updates are Firefox 3 ones and the other 2 are xulrunner.

---

### Post by jelcoward on 2009-05-08
I have the same problem - new upgrade to Jaunty.  In the upgrade I chose to keep my previous fstab file......and I think that might be the problem because when trying to update the 'broken' Jaunty from the command line I get 'is /dev/pts mounted?'  or similar (away from the machine right now.  I have seen a fix involving adding a line to fstab - which I don't quite recall - but I think was a line to mount pts.  My theory being that Jaunty needs that line but previous releases didn't.  If I track down the fstab line I will post here.

---

### Post by jelcoward on 2009-05-08
My theory was incorrect (but along the right lines, I say in my humble defence :)

The answer is that you need both of the following.

There is an init script:
/etc/init.d/mountdevsubfs.sh
that deals with mounting the required devpts filesystem. Do you have that file?

**check you have that file by doing ls /etc/init.d   the file should appear in the list**


Do you also have the symlink at:
/etc/rcS.d/S11mountdevsubfs.sh

**check this with ls /etc/rcS.d  you should see the symlink listed there**

This info was from 
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/338071](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/338071)

...towards the bottom there are fixes. The bit of the fix not described is how to create the the symlink in /etc/rcS.d but Mrs Google can likely fill you in on that.
Hope that helps.......I'm just a linux newbie too :)

---

### Post by m.ayad on 2009-06-04
you shoud add devpts to fstab (etc/fstab)

```
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
```

and after that you should remount by running as root 

```
mount -a

exit
```

---

