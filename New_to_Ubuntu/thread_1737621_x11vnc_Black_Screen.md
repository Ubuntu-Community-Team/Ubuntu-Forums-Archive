---
title: "x11vnc Black Screen"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by MarkTrent on 2011-04-23
Hello,

I've got x11vnc installed on my Ubuntu box but when I connect remotely all that's displayed on my client is a black screen and a cursor. If I move the mouse connected to my Ubuntu box the cursor also moves on the remote client and vice versa so the connection is definitely there.

I'm running it as a headless box at the moment, **BUT**, if I do have a monitor connected to the Ubuntu box then the remote connection does work perfectly. Does anyone know how I can get the remote connection to work properly without requiring a monitor attached?

Thanks,
Mark

---

### Post by SteveDee on 2011-04-23
> **MarkTrent said:**
> ...Does anyone know how I can get the remote connection to work properly without requiring a monitor attached?


What version of Ubuntu are you running?

In previous versions you needed to modify the xorg.conf file (See: [http://ubuntuforums.org/showthread.php?t=1586016&highlight=headless](http://ubuntuforums.org/showthread.php?t=1586016&highlight=headless))
...but in 10.10 this does not seem to be necessary.

---

### Post by MarkTrent on 2011-04-23
I'm using 10.10.

My x11vnc startup is as follows if this helps:

```
/usr/bin/x11vnc -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900

```

---

### Post by dwasifar on 2011-04-23
Are you by any chance using the nVidia proprietary video drivers?  Last time I tried to set up a headless box with those drivers installed I could never make it work.  The open drivers didn't have that problem, but with the proprietary drivers the machine wouldn't even boot unless there was a monitor attached.  It could be powered off, but it had to be there.

---

### Post by MarkTrent on 2011-04-23
> **SteveDee said:**
> What version of Ubuntu are you running?

In previous versions you needed to modify the xorg.conf file (See: [http://ubuntuforums.org/showthread.php?t=1586016&highlight=headless](http://ubuntuforums.org/showthread.php?t=1586016&highlight=headless))
...but in 10.10 this does not seem to be necessary.

Thanks Steve this solved the problem.

> **dwasifar said:**
> Are you by any chance using the nVidia proprietary video drivers?  Last time I tried to set up a headless box with those drivers installed I could never make it work.  The open drivers didn't have that problem, but with the proprietary drivers the machine wouldn't even boot unless there was a monitor attached.  It could be powered off, but it had to be there.

No I was using ATI drivers.

---

