---
title: "CPU at 100% with no processes?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by togril2010 on 2010-01-07
Macbook pro 3.1 core 2
Ubuntu Karmic

My CPU 2 is at 100 % with no real processes going on (no apps running - mem usage 12.6% of 3.9 gig)). 

I noticed the fan came on and came to see why...

Am concerned about this kind of thing damaging my cpu, as I leave the computer unattended (thinking that power saver kick in).

is this er...normal? 
Thus far I have non working laptop keyboard (see previous post) and now this. 

Concerned of Sydney.:shock:

---

### Post by sanderd17 on 2010-01-07
Can you see which process is using most of the cpu usage? or can't you see a process?

Did this happen with the live cd too? or is it just recently?

---

### Post by lotharmat on 2010-01-07
Open a terminal and type 

```
top
```

See if there are any processes running that are taking up a great deal of cpu.

---

### Post by togril2010 on 2010-01-07
Thanks - restarted in the end - looked at the processes (gui) but didn't see anything untoward.
Will 'top' if it happens again (I only knew ps -e).
It was only on cpu 2 -

@[sanderd17]("http://ubuntuforums.org/member.php?u=742644") - don't remember happening on the live cd.
in the meantime have downloaded the beginners guide....:)

---

### Post by 3rdalbum on 2010-01-07
Running your CPU (or one core) at 100% will not damage it, no matter how long it runs like this for. The CPU is certified for that particular speed in sustained operation, and the cooler fans are certified for that particular heat output too.

Even if your fans stopped running, both Linux and the CPU itself are designed to shut down the computer before damaging overheating can take place. Linux tries to shut down normally before the CPU's own "turn-off-right-now" system is activated.

When you next get the problem, use the 'top' command to see what's thrashing the CPU and then kill the offending process.

---

### Post by r+9 on 2010-01-11
try to find the vino-server process and kill it

it's just a chance, and it won't show up as using your CPU very hard but killing it has had some success for me

---

### Post by togril2010 on 2010-01-17
Hey, Thanks all -   it's good to know the cpu won't get creamed.
I found the process, but don't have it in front of me at the moment:
it's video input (cheese and stopmotion using the inbuilt cam) that created it.
I'll run the apps again and get the process - I AM running this on a macbook pro, so it could be specific to this machine. 

Slowly getting to grips wiv linux. I like it now. :D

---

