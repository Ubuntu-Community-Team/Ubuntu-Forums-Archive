---
title: "Ubuntu running slowly..."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Adamantus on 2009-01-25
Hey, 

I moved to Ubuntu 8.04 from Vista because I was told Linux in general is much faster, but I've noticed quite the opposite. Boot up time is significantly shorter, but program opening times are about the same or even longer than Vista. What annoys me more is that I just installed Linux Mint (Elyssa) on my girlfriend's computer, and it is much faster than mine. It's even weirder because she has an old Gateway: 1.8 GHz processor with 1 GB memory whereas I have a new HP dv5-1004nr with a 2.1 GHz processor and 4 GB of memory (although I only use 2.7 because I'm running 32 bit Ubuntu). 

Starting up Firefox takes me about 2-3 seconds the first time after startup (about 1-2 seconds afterwards), Thunderbird about 3-4 seconds, and Openoffice about about 3-4 seconds (about 1 second afterwards). Although these aren't terribly long times and I don't see any significant decrease even having tons of things open, my girlfriend's load times are usually only half as long (usually instantaneous). What's the difference that could be slowing down my computer? I was hoping with a computer as fast as mine that things would open instantaneously.

---

### Post by sdennie on 2009-01-25
Maybe Mint is aggressively preloading things into cache.  You may be able to emulate that behavior with:

```

sudo apt-get install preload

```

It won't make an immediate difference but, as preload learns what you are using, you will notice a difference.

Also, you may be able to fix your 1.3G of wasted memory by reading this: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by AlexGryson on 2009-01-25
I had some similar issues when I moved from vista to Ubuntu about three months ago. As such, I'm still a newbie and can't give you any specific help, but my own performance issues were solved through tweaking. Once that was done my laptop now works better than it ever did under vista, and it's even better than my xp partition (for gaming). 
Long story -> Short story
Don't judge your system until it's tweaked! :D
Could you post more details about your system? 
That way other posters (less nooby than me) can help you out.
A great resource for me int his regard was:
[http://www.ubuntukungfu.org/](http://www.ubuntukungfu.org/)

---

### Post by Adamantus on 2009-01-25
The only other thing I could think to say is that I have a CPU frequency scaling monitor enabled (powernow). I usually have it "ondemand" which keeps my CPU running about 500 MHz, but it jumps up to 2.1 GHz when I open a program or watch a movie. But I don't think this is the problem, since it was running just as slowly before I enabled the scaling governor.

---

### Post by sdennie on 2009-01-25
The scaling governor is almost certainly not the problem.  It can go from min to max speed so fast that it's impossible to notice for the vast majority of people.  It's on the order of microseconds to change CPU frequency for most chips.

---

