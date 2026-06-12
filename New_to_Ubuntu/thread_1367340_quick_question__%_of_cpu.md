---
title: "quick question:  % of cpu"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-29
I'm running the system monitor, and I realize that I don't know the meaning of the cpu history.  I didn't know that my computer could use a fraction of the cpu without using the whole chip.  Can someone please explain what is the meaning of percentage in the case of cpu history?  For example, I don't know whether a high cpu percentage means that my computer is running faster or is getting bogged down by resource usage.

a related question:
Is the usage integrated or sampled?

---

### Post by ovid9 on 2009-12-29
> **MichaelBurns said:**
>  For example, I don't know whether a high cpu percentage means that my computer is running faster or is getting bogged down by resource usage.
 

 
*A high CPU % doesn't mean its running faster or slower. Its just the total % of the CPU's capacity currently being used. *

*If you're using 95% of your CPU chances are programs are going to run slower as the CPU is under heavier load, but it doesn't mean the CPU itself is going slower or faster.*

*This is a very simplistic answer, and others can probably say more on it, but from what I understand, that's it in a nutshell.*
 
Edit: And just ignore what I said above.

---

### Post by doas777 on 2009-12-29
strangly enough, you are not using a fraction of the CPU, but that in any given second, the CPU is idle for a percentage of the time. if it is processing for 1/2 a second, then you get 50% usage. the history is just the totals for each of the previous seconds.

---

### Post by ovid9 on 2009-12-29
And my understanding was wrong.  This really doesn't surprise me.  lol
 
Interesting.

---

### Post by MichaelBurns on 2009-12-29
Thanks, doas.  I don't know why I couldn't think of that painfully obvious answer.  I will wait to mark this one solved just in case others have some more valuable input.

---

### Post by Bartender on 2009-12-29
I don't have much confidence in System Monitor.  Even on a fairly powerful machine the simple act of running System Monitor seems to put 10% load on the CPU. 

Here's a fun little test - start up System Monitor.  Now fire up a terminal and type in "top".  Just those three letters, t-o-p.  Enter.  top gives you a list that constantly updates itself, showing CPU usage and RAM usage.  It's not graphic like System Monitor, but it identifies the applications that are using the most resources, which is kind of interesting.  

Now wiggle your mouse around and watch CPU usage jump in System Monitor and top.  Start a program, whatever, this all gives you an idea of what the above posters described.

Leave top up, and turn off System Monitor.  Watch the CPU usage drop in top.

---

### Post by MichaelBurns on 2009-12-29
Interesting.

It did strike me as odd that system monitor alone should "consume 10% of the cpu".  At a somewhat unrelated suggestion, I increased the update times considerably, and then the cpu went down to 4%.  But that doesn't quite explain it, because I believe top updates about once per second as well, which is the default for system monitor, so something else is making system monitor greedy.

---

### Post by doas777 on 2009-12-29
GSM uses the Cairo engine for it's graphs, which causes some draw on the CPU. I use htop or top most of the time.

I also find that the panel applet for GSM doesn't cause lag, so I just have it sitting there showing CPU, Ram, Network, Load, and IO. that fulfills most of my needs. many people use conky for the same thing.

---

### Post by blur xc on 2009-12-29
> **Bartender said:**
> I don't have much confidence in System Monitor.  Even on a fairly powerful machine the simple act of running System Monitor seems to put 10% load on the CPU. 

Here's a fun little test - start up System Monitor.  Now fire up a terminal and type in "top".  Just those three letters, t-o-p.  Enter.  top gives you a list that constantly updates itself, showing CPU usage and RAM usage.  It's not graphic like System Monitor, but it identifies the applications that are using the most resources, which is kind of interesting.  

Now wiggle your mouse around and watch CPU usage jump in System Monitor and top.  Start a program, whatever, this all gives you an idea of what the above posters described.

Leave top up, and turn off System Monitor.  Watch the CPU usage drop in top.

On my windows machine, wiggling the mouse makes the cpu usage jump as well, as does moving a window around on the screen.  Idling, my cpu usage is 4 - 8%, and wiggling the mouse around gets it up to around 60%.  I can recall years ago on an older, crappier computer, being able to peg the cpu up around 100% by wiggling the mouse.  I think that's normal (normal as in, it's what's I'm used to seeing on a variety of computers).  My question is why?  Why does wiggling the moue or dragging a window around make the cpu usage spike like that?

BM

---

### Post by doas777 on 2009-12-29
> **blur xc said:**
> On my windows machine, wiggling the mouse makes the cpu usage jump as well, as does moving a window around on the screen.  Idling, my cpu usage is 4 - 8%, and wiggling the mouse around gets it up to around 60%.  I can recall years ago on an older, crappier computer, being able to peg the cpu up around 100% by wiggling the mouse.  I think that's normal (normal as in, it's what's I'm used to seeing on a variety of computers).  My question is why?  Why does wiggling the moue or dragging a window around make the cpu usage spike like that?

BM


short answer, it shouldn't. most of my win boxes idle at > 0.77% cpu, and manipulating the desktop consumes no noticable resources (process explorer is set to a .25% min threshold, so anything below that goes unnoticed. procexp takes about 1.54% to run).

sounds like your CPU may be doing a lot of work that could be handled by a decent vid card.

---

### Post by blur xc on 2009-12-29
> **doas777 said:**
> short answer, it shouldn't. most of my win boxes idle at > 0.77% cpu, and manipulating the desktop consumes no noticable resources (process explorer is set to a .25% min threshold, so anything below that goes unnoticed. procexp takes about 1.54% to run).

sounds like your CPU may be doing a lot of work that could be handled by a decent vid card.

It's got an intel core 2 extreme 2.8ghz cpu, nvidia quadro fx 3600m w/ 512mb video ram.  At the time it was the most you could get in a laptop form dell.  Cost like $5k.

BM

---

### Post by FinalCoyote on 2009-12-29
Haha, this is quite hilarious.

Still, it's not as if Linux runs incredibly fast on my gear anyway, so to hell with it

---

### Post by doas777 on 2009-12-29
> **blur xc said:**
> It's got an intel core 2 extreme 2.8ghz cpu, nvidia quadro fx 3600m w/ 512mb video ram.  At the time it was the most you could get in a laptop form dell.  Cost like $5k.

BM
a workstation card? I don't know if I have ever seen one of those in the wild, except on a mac. you're right, those are decent specs. perhaps a software issue.

---

