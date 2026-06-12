---
title: "kill x server and maintain terminal process?"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by mzycdth on 2011-07-17
Hi guys,  Is this possible? Can I stop X but maintain a process (dd) running in terminal? It's cpu limited and is going to take 25hrs at the current rate. I'm hoping killing X may free up some resources to speed that process slightly.  Thanks in advance

---

### Post by CatKiller on 2011-07-17
If you'd started it in [screen]("http://en.wikipedia.org/wiki/GNU_Screen"), it would be easy; you just detach from the process, kill X, then re-attach to the running process again. My command-line-fu isn't great enough to know if it's possible any other way.

---

### Post by mikejonesey on 2011-07-17
```
kill -l
```for all vail sigs, you will want to use SIGSTOP (19);

this is the same as using Ctrl+z from command line;

it will then be paused...

then to resume, where you would usualy use bg or fg to bring a process back to life you'd use SIGCONT...

:)

ps for what it's worth i'd go the route of renice rather than  pausing x...

```
sudo renice (only root can renice to below 0) -5 PID
```

---

### Post by jwbrase on 2011-07-17
> **mzycdth said:**
> Hi guys,  Is this possible? Can I stop X but maintain a process (dd) running in terminal? It's cpu limited and is going to take 25hrs at the current rate. I'm hoping killing X may free up some resources to speed that process slightly.  Thanks in advance

Depending where you're copying from and to, I'd say that dd is most likely *not* CPU limited, but disk I/O limited. Killing X, as a rule, won't help it much.

If you open up another terminal and run the program "top", you should see a line that looks like this:

```
Cpu(s):  1.5%us,  1.1%sy,  0.0%ni, 97.1%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
```

You will probably find that the "wa" number is very high.

That number tells you how much time the CPU is spending twiddling its thumbs while the disk takes its sweet time transferring data. Disk access is ***slow***.

---

### Post by mzycdth on 2011-07-18
Cheers guys, thats excellent. jwbrase you're right, I hadn't considered that (I thought the only bottlenecks for writing were usb transfer speed and disk write speed). catkiller and MikeJonsey, I will use that terminal trickery in future no doubt!

---

