---
title: "Clock keeps quitting unexpectedly"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by lanetherif on 2010-05-06
Hi,
I keep getting an error message that informs me that "Clock has quit unexpectedly" and asks me whether I want to reload it or not. It seems to happen when I leave pc for a few minutes, as far as I remember it never happened when the pc was actively in use. 

Any ideas?

---

### Post by lanetherif on 2010-05-07
No ideas? :D

---

### Post by lanetherif on 2010-05-08
Really, ubuntu forums?
 At least give me a clue... :D

---

### Post by kako13 on 2010-05-10
I have the same problem.

---

### Post by cariboo on 2010-05-10
Have you tried:

```
kill-all gnome-panel
```

---

### Post by lyall on 2010-05-10
How old is your PC?

if it is over three years old it might be your CMOS battery

weird things can happen before the battery dies

good luck and have fun learning

---

### Post by lanetherif on 2010-05-11
> **kako13 said:**
> I have the same problem.

Exactly this! 
When should I use kill all command? I mean when there is no error or when the error shows up?
My computer is fairly new, I don't think it is about the cmos battery.

---

### Post by lanetherif on 2010-05-11
> **cariboo907 said:**
> Have you tried:

```
kill-all gnome-panel
```

I have tried it anyway. :)
I got this message: > No command 'kill-all' found, did you mean:
 Command 'killall' from package 'psmisc' (main)
kill-all: command not found


update: I tried it as killall. Yet, the problem persists.

---

### Post by gdonwallace on 2010-05-14
I'll add my voice to this as well.  I am having the same problem.

Not sure what causes it, but it is the caused by a child process continuing to run after a parent process has either stopped running, or stopped due to an error.  I found this by running the TOP command, and found a zombie process.  I used this ps axo stat,ppid,pid,cmd | grep ^Z to get the PPID of the zombie process and killed it with the -9 flag, and it asked me to restart CLOCK.

Because the zombie process is causing my system to slow down when I try to do anything, I know when it happens, just don't have any clue to what is causing it.

---

### Post by lanetherif on 2010-05-17
I am not sure whether it is due to this, but after not reloading clock when the prompt screen popped out, I manually added it to the panel and it now seems to work right. If you didn't up to now, you might want to give it a chance.

---

### Post by TippMoseley on 2010-05-19
Adding multiple locations while disconnected from the internet is a reliable reproducer for me.  The first seems to be ok, but the second will trigger a crash.

---

