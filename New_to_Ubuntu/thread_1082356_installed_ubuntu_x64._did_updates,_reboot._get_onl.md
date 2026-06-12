---
title: "installed ubuntu x64. did updates, reboot. get only command line"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by phillyd on 2009-02-27
I installed Ubuntu x64 on my Dell Optiplex 755.  Install went fine no errors.  I rebooted, and then went into the gui.  I installed updates and installed vmware player.  I rebooted, and now can only get the command line.  I typed in startx and got this:

xauth: creating new authority file /home/vm-machine/.Xauthority
xauth: creating new authority file /home/vm-machine/.Xauthority

exec: 5: /usr/bin/X11/X: not found
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
Xinit: No such process(errno 3): Server error.

---

### Post by thtrgremlin on 2009-02-27
Were you using an alternative install?

Been playing around with X quote a bit recently. startx and X are part of the package 'xorg', but I wonder if the desktop was not installed.

Most likely I would guess (without knowing more) you need to:```
sudo apt-get install ubuntu-desktop
```

If that doesn't fix it, can investigate further.

---

### Post by phillyd on 2009-03-04
This did the trick.

Thanks much for your help.

---

