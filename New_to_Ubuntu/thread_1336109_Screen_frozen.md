---
title: "Screen frozen"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-24
After playing around with the volume preferences, the screen now freezes after booting up. The mouse is completely dead. I do not have a clue what to do. I hate to re-install Ubuntu 9.10 everytime I have a problem. Is there a way to repair this?

Thanks

---

### Post by ikt on 2009-11-24
Hello :)

99% of the time there is a way to fix an issue, the only problem is deciding if it is worth the time to investigate and try and repair or just reinstall.

If you hold down shift while the pc is booting up should give you the GRUB menu, if you see the option for 'Recovery mode' or something similar hit that, and you should probably end up at the terminal prompt.


```
cd /var/log
```

```
vi syslog
```

and scroll through the log file, I would look for any sort of messages that stand out, such as 'error loading', or anything particular.

If anyone knows how to disable the proprietary graphics driver from recovery mode that's probably what I'd do next.

---

### Post by daniell59 on 2009-11-24
> **ikt said:**
> Hello :)

99% of the time there is a way to fix an issue, the only problem is deciding if it is worth the time to investigate and try and repair or just reinstall.

If you hold down shift while the pc is booting up should give you the GRUB menu, if you see the option for 'Recovery mode' or something similar hit that, and you should probably end up at the terminal prompt.


```
cd /var/log
```

```
vi syslog
```

and scroll through the log file, I would look for any sort of messages that stand out, such as 'error loading', or anything particular.

If anyone knows how to disable the proprietary graphics driver from recovery mode that's probably what I'd do next.

I can get to the grub menu, then I am lost. I don't have a clue about writing commmands.
As I previoulsy mentioned, I don't want to be constantly re-installing Ubuntu. It seems to run well until I try to expand my knowledge by trying new things.

Thanks for the help

---

### Post by ikt on 2009-11-25
> **daniell59 said:**
> It seems to run well until I try to expand my knowledge by trying new things.

Ah! The best thing for this is virtualbox!

[http://www.virtualbox.org/](http://www.virtualbox.org/)

and a quick guide:

[http://www.youtube.com/watch?v=n5ravk1H6DM](http://www.youtube.com/watch?v=n5ravk1H6DM)

Lets you install ubuntu in sort of a sandbox for itself, so you can muck around and not a problem if you mess it up!

---

