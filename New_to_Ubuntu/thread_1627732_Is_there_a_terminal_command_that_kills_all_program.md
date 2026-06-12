---
title: "Is there a terminal command that kills all programs open."
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Jetso on 2010-11-21
I would like to know if there is a command in terminal that kills all programs and makes it like the computer has just started the session. I would use this in a script. Thank you!

---

### Post by Jetso on 2010-11-21
I would also like to say that I am not a very "advanced" user at Linux, although I would like to be one, I just started, and am trying to learn bash scripting.

---

### Post by northern lights on 2010-11-21
Killing all running processes would shutdown your system.

Listing all running processes:```
ps aux | less
```

Killing processes by PID or name: [man killall]("http://manpages.ubuntu.com/manpages/maverick/man1/killall.1.html")

---

### Post by tgalati4 on 2010-11-21
Well, the process "init" is the mother of all processes.  It is typically Process #1.  Killing it is generally a bad thing.  There are however several things that you can do with init:

man init
man initctl

You can also boot your system clean, run the following:

ps -ef

Note the highest process number for a clean boot, then simply write a script that deletes all processes greater than that number.  This may not work all the time because each time you boot, there could be some housekeeping processes running that will change the baseline process number somewhat--so it is not 100%.  You are looking for an elegant way to do this, and short of logging out and logging back in, I don't know of a clean way to do this.

Perhaps if you explain the use case in some detail, we can provide better options.

---

