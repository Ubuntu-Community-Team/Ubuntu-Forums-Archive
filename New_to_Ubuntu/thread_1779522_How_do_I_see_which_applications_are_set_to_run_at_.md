---
title: "How do I see which applications are set to run at boot time ?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-10
How do I see which applications are set to run at boot time ?

---

### Post by papibe on 2011-06-10
Not exactly at boot time, but you can see and sort of manage apps that run right when you login: System -> Preferences -> Startup Applications.

Regards.

---

### Post by kalimojo on 2011-06-11
bump

---

### Post by 3rdalbum on 2011-06-11
The only user-level programs that run automatically are the ones listed in the Startup Applications window (more accurately, they are login applications).

Why do you need to know what is starting up at boot time? The boot-init system in Ubuntu (called Upstart) is designed to start services if and when they are needed, rather than just starting everything that you might possibly need. I don't think you could shave more than a second or two off your boot time by playing around with it, and you're more likely to end off with an unbootable system.

If you can answer why you need to know what services are starting, then we might be able to figure out what you need to know; but I'd be very hesitant to tell you how to fiddle with this and then have to give you support when you break your system.

---

### Post by grahammechanical on 2011-06-11
Try Log File Viewer in System Settings. Do not ask me to explain what you see there. Log File Viewer will let you copy what is displayed but it does not give you any control over what is run at boot time (at least I do not think so).

Regards.

---

### Post by apollothethird on 2011-06-11
> **kalimojo said:**
> bump

Hi, Kalimojo.  You could consider showing respect to the users who are trying to help you.  Your question is quiet vague.  Lot's of things are built into the kernel.  It'd take a lot of work to look at what happens in the kernel.  Many of those things you won't want to tamper with.  There are many things that start up on the fly by loading modules later that you don't want to have running if they aren't needed.

It would be great if you would contribute back to the community by giving us more to go on, as one of the previous users has suggested.

You can also consider running

```
chkconfig --list
```You might notice from that list that some things start at various runlevels and quit.

Looking for something for a specific reason would really make more sense than asking an open question that can be interpreted in many ways, then ignoring the suggestions given to you by the users who are trying to help.

You can consider expressing appreciation to the first user.  The next time you have a question he might be the first one to read it and an expression of appreciation would inspire him more to take the time to help you.  There's even a good chance that he might have the best answer for whatever specifically you're looking for, and would give it to you just as quick as he tried with your vague question if you showed appreciation.  He'd more likely get a notice with each update to this tread if your attitude hasn't caused him to cancel notices to this thread's updates.

Hope you get your problem solved!  Wish I knew what it was.

Have a nice day.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by kalimojo on 2011-06-11
SOrry if i seem a bit vague, in system monitor i see bluetooth-applet running, i dont have bluetooth so dont need it. just wondering how i can prevent it loading at boot,

OK, I see it under system-> preferences -> startup applications and unchecked it,

thanks for your kind patience

all the help i get here is greatly appreciated

---

