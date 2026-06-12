---
title: "Recovering Data/Restoring Bad Installation"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by chinggisk on 2010-09-23
Hokay, so:

I think I've pretty much borked my system.  What happened was I was running Ubuntu 9.10 64-bit and it was running alright except for some graphics problems.  Over the course of trying to fix those I eventually got fed up with it and decided to just upgrade to 10.04, hoping I could get everything to work better there.  The upgrade went through but had a boatload of errors come up, and now the system won't boot all the way.  Here's what I get:

```
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory
mountall: invalid option: --tmptime=0
Try 'mountall --help' for more information.
init: mountall main process (451) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
```

Obviously I'm a total Linux noob who has no idea what he's doing.  At this point I don't mind just wiping it and starting over except there are a few files that I'd really like to get off before doing so.  I can see them if I boot using my Live CD but it says that I don't have permission to access them.  Any suggestions?  Thanks.

---

### Post by ajgreeny on 2010-09-23
I don't think I can help with the update problem, but if you open nautilus in the live CD with the command ```
gksudo nautilus
``` using the Alt+F2 run dialog or terminal if you are happy with that, you should be able to copy all the files you need from the old ubuntu home to a usb disk or other place for backup.

---

### Post by chinggisk on 2010-09-23
That seems to have done the trick.  Thanks much!

---

