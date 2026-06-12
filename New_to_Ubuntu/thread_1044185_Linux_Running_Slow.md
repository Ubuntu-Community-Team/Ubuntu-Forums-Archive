---
title: "Linux Running Slow"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by RussW210 on 2009-01-19
Ubuntu has been getting a bit slow lately.  When I have multiple programs running, everything runs super slow.  Most noticeably is when I have k9copy running and backing up one of my dvd's no other program will run at the same time.  They will freeze, have huge lag.

This has only been happening recently, maybe over the past 2 weeks.  My computer is 4 months old (as is Linux on my computer) and has a quad-core processor with 3gb of RAM so all this lag is not because my computer is under spec.  My system monitor says RAM is only at 14% and that my processor isn't under any stress.

The one thing I can think of here is that maybe my cache is full?  Or something like that?  I only experience lag when there are multiple programs running (which never did before).

I haven't been entering any terminal commands to do any cleaning.  And haven't been able to find a list of terminal commands I should enter every once in a while to keep my computer clean and running smooth.  Does anyone have a list of commands I should be entering to keep this computer clean?  Something like 'sudo apt-get autoclean' and 'clean'?

Thank you very much for your help!

---

### Post by yeats on 2009-01-19
Some useful terminal commands for system monitoring:

```
top
```

will let you know which programs are using the most resources.  Typing "1" will toggle between specific processor loads and the overall system load.  A handy way to see all the available commands, etc. is to look at top's manual page:

```
man top
```

If you're concerned about disk usage, these two commands help with that:

```
df -h
du -h
```

"df -h" creates "human readable" (hence the "h" flag) information about each partition's disk usage.  "du -h" creates a lot of output and would likely be best used by piping into a pager program like less:

```
du -h | less
```

or if you know the file you're looking for:

```
du -h | grep [*file name*]
```


Hope that's helpful.

---

### Post by yeats on 2009-01-19
One more thing about "du -h" :-) - it starts looking from whichever directory you are currently in, so if you want to see specific files' disk usage throughout your entire system, make sure to

```
cd /
du -h
```

---

### Post by RussW210 on 2009-01-19
Thank you Chris, that is very helpful information in identifying the problem.  Appreciate the help, have a good day.

---

### Post by yeats on 2009-01-19
Anytime - good luck. :-)

---

### Post by linux_tech on 2009-01-19
this explains some commands to clean up;  how to remove partial packages, etc

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

