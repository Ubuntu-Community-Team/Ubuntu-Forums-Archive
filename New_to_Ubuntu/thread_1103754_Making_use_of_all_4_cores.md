---
title: "Making use of all 4 cores"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by kazza765 on 2009-03-23
Hi all,

I've searched the forums and couldn't find the answer to this question anywhere. Apologies if it has been posted before.


I currently run some simulations on the computer bank that we have the university. The simulations are fairly simple FORTRAN programs, but very CPU intensive. I just run these in a terminal window in Ubuntu, and use multiple computers to run several simulations simultaneously.

I have a quad-core computer at home, and would like to use it for work stuff. I know that more sophisticated programs will automatically make the most of 4 processors, but this isn't a sophisticated program. If I install Ubuntu on it, is there any way to get 4 terminal windows each using a separate processor, so that running 4 simulations simultaneously will take full advantage of the quad core? Or will Ubuntu work this out for me automatically, even though it's only a very simple program running in a terminal window?

Thanks

---

### Post by SunnyRabbiera on 2009-03-23
It should see all 4 cores no prob, the linux kernel is very diverse.

---

### Post by mcduck on 2009-03-23
> **kazza765 said:**
> Hi all,

I've searched the forums and couldn't find the answer to this question anywhere. Apologies if it has been posted before.


I currently run some simulations on the computer bank that we have the university. The simulations are fairly simple FORTRAN programs, but very CPU intensive. I just run these in a terminal window in Ubuntu, and use multiple computers to run several simulations simultaneously.

I have a quad-core computer at home, and would like to use it for work stuff. I know that more sophisticated programs will automatically make the most of 4 processors, but this isn't a sophisticated program. If I install Ubuntu on it, is there any way to get 4 terminal windows each using a separate processor, so that running 4 simulations simultaneously will take full advantage of the quad core? Or will Ubuntu work this out for me automatically, even though it's only a very simple program running in a terminal window?

Thanks

If it's just a single program you wish to run, and it's not multi-threaded, then it will only run on one processor/core.

If possible, open 4 terminals and start four instances of your program at once. That way you'll have 4 process that will each run on their own processor core.

Ubuntu won't automatically start multiple processes for you, but if you start them yourself the system will of course balance the load between all available processors/cores.

---

### Post by kazza765 on 2009-03-23
Terrific, thanks. That's what I was hoping to hear.

---

### Post by boof1988 on 2009-03-23
> **mcduck said:**
> If it's just a single program you wish to run, and it's not multi-threaded, then it will only run on one processor/core.

If possible, open 4 terminals and start four instances of your program at once. That way you'll have 4 process that will each run on their own processor core.

Ubuntu won't automatically start multiple processes for you, but if you start them yourself the system will of course balance the load between all available processors/cores.

I have done something similar to this (and it seemed to work as desired).  I opened two instances of soundconverter and Ubuntu seemed to use about one core for each open application.

Please let us know if you're able to get all four cores working by opening the four different instances of you application.

---

### Post by kazza765 on 2009-03-25
> **boof1988 said:**
> I have done something similar to this (and it seemed to work as desired).  I opened two instances of soundconverter and Ubuntu seemed to use about one core for each open application.

Please let us know if you're able to get all four cores working by opening the four different instances of you application.

Ok, I've just found system manager, and I can confirm that this works exactly as I had hoped. Each new instance of the program starts running on a separate core.

---

### Post by Chemical Imbalance on 2009-03-25
> **kazza765 said:**
> Ok, I've just found system manager, and I can confirm that this works exactly as I had hoped. Each new instance of the program starts running on a separate core.

If you want a desktop app to keep track of the cores' usage, then gkrellm might be useful:

```
sudo apt-get install gkrellm
```

[ATTACH]107625[/ATTACH]

Just add "gkrellm" to  "Sessions" to start up on login. 
Right-clicking on gkrellm will allow you to configure it.

---

### Post by kpatz on 2009-03-25
Sort of on the same topic, is there a way to determine what core(s) a process is using, other than the "guess" method?  (e.g. launch app, see which cpu usage goes up)?  Something in ps, top, or htop?  I haven't found anything that gives me that info...

---

### Post by TheguywholikesLINUX on 2009-03-27
I have a similar problem as I am thinking of upgrading from my Celeron D 3.2ghz to a 2.66 ghz Quad, however if only the first core is used then i will have a slight decrease in performance. I have heared that Mac OS X can run different app's on different cores automatically, it seems Ubuntu can do this, but can i get it to run apps by default on core 2 3 or 4, and keep core 1 for gui kernel window manager and all the rest of it. Also can i start an app on a core of my choice? How soon does multi core support take place, will is work from soon in start up so I can do boot faster?

Thanks in advance!

---

