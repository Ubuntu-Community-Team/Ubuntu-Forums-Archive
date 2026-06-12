---
title: "I broke my home folder!  Help!"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by pvfjr on 2009-09-24
So I was using the psychocats guide for moving my home folder to a separate partition.  It was going ok, until I tried to edit my fstab. The command I gave was:
gksudo gedit /old/etc/fstab


All I'm getting is:

Error copying '/home/paul/.Xauthority' to '/tmp/libgksu-KN6zSZ': No such file or directory


What gives?  Now some changes have already been made, the old home folder paths have changed I guess, so I don't have the new one or the old one now.

---

### Post by nothingspecial on 2009-09-24
I`m not with you here.

You issue the command ```
gksudo gedit /old/etc/fstab
``` and you get the error
```
Error copying '/home/paul/.Xauthority' to '/tmp/libgksu-KN6zSZ': No such file or directory
```?

Or is that error from a different command.

---

### Post by khelben1979 on 2009-09-24
```
sudo df -h
```
will give us some information about the sizes of your partitions, then we will see better how it looks like.

---

### Post by pvfjr on 2009-09-24
Well I got it figured out.  I had to undo the move to home_backup, put everything back where it was (which was a challenge for me in terminal), then reboot.  And wouldn't you know it, I started over, got it all done, restarted, then had the stinking permissions issues and had to do all that chown stuff.  But it works now, no data lost, and I'm happy!  I just wish I would have dumped the 20 gigs of crap I had in my trash folder before I did this.  Kinda sucked sitting there waiting for a bunch of trash to copy itself to a new location.  Thanks for your replies.

---

### Post by pvfjr on 2009-09-24
> **nothingspecial said:**
> I`m not with you here.

You issue the command ```
gksudo gedit /old/etc/fstab
``` and you get the error
```
Error copying '/home/paul/.Xauthority' to '/tmp/libgksu-KN6zSZ': No such file or directory
```?

Or is that error from a different command.
Yep, that was the issue.  What I didn't realize is that it was the step before that one that went awry. On one try, I actually did get fstab to open, and it was completely blank!

---

### Post by scorp123 on 2009-09-24
> **pvfjr said:**
>  It was going ok, until I tried to edit my fstab. The command I gave was:
gksudo gedit /old/etc/fstab


All I'm getting is:

Error copying '/home/paul/.Xauthority' to '/tmp/libgksu-KN6zSZ': No such file or directory

What gives? You tried to start a X11 application ... but with your $HOME folder gone to another location the system doesn't know any longer if you're really authorized to use GUI stuff or not. Hence the error.

You should not have done this stuff in GUI ... But OK, glad you figured it out and fixed it. Respect. =D>

---

### Post by nothingspecial on 2009-09-24
> **scorp123 said:**
> You tried to start a X11 application ... but with your $HOME folder gone to another location the system doesn't know any longer if you're really authorized to use GUI stuff or not. Hence the error.


Ahh, that makes sense, Thanks.

---

### Post by pvfjr on 2009-09-29
Well I was using terminal, so are you saying I should have booted to a terminal instead?  Either way, it's done now.  It was a little scary, but I blundered my way through it.  Thanks for the help.

---

