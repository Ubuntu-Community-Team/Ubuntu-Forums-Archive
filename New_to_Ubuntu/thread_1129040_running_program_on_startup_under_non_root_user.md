---
title: "running program on startup under non root user?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by miko3k on 2009-04-18
hi,

I would like to run a daemon under non-root user (demon itself is implemented as perl script). I know I should create a script in [FONT="Courier New"]/etc/init.d[/FONT] which starts the daemon, however I'm not sure how to properly drop root privileges. [FONT="Courier New"]su <user> -c <command>[/FONT] could help, but it does not seem to be a right way to me.

Any suggestions?

---

### Post by Bachstelze on 2009-04-18
A better way to do this would be to make a cronjob with the special [font="monospace"]@reboot[/font] startup time. For example,here's my line to start [font="monospace"]fetchmail[/font] for my user account when the system starts:

```
@reboot fetchmail -d 300 &> /dev/null
```

---

### Post by miko3k on 2009-04-18
thanks! Look like a much better way to do the job. On the other hand, I'm quite sad to give up all the great debian boot script magic :)

---

