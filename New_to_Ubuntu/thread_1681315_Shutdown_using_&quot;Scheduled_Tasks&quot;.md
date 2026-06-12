---
title: "Shutdown using &quot;Scheduled Tasks&quot;"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by dhochmuth on 2011-02-04
I'm trying to use "Scheduled Tasks" to shut down my machine.  After searching a bit, I tried entering this as the task/command:

sudo shutdown -h now

But nothing happened at the designated time.  If anyone can help this poor newbie, I'd appreciate it.

---

### Post by sikander3786 on 2011-02-04
```
sudo shutdown -h now
```

This command should shutdown the system right now. Are you typing your password in the Terminal? It won't return any characters or asterisks, type blindly and hit <Enter>.

You can also use some other syntax like,

```
sudo shutdown -h +60
```

Where 60 is time in minutes and it would shutdown your PC after an hour.

```
sudo shutdown -h 11:00
```

Where 11:00 is the time on a 24 hour clock and it would shutdown your PC at 1100 hours.

Or, simply install the pacakge 'gshutdown' from Software Center. It would appear under Applications > Accessories or Applications > System Tools I think and is a handy application for scheduled shutdowns.

---

### Post by DiSTORT3D on 2011-02-04
several command to terminate it.
```

shutdown -h (0) is now or any other time (1) 1 minute

shutdown -h now

halt

poweroff

init 0

```for restart
```

shutdown -r now

reboot
```

---

