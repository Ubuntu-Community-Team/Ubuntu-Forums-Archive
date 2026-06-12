---
title: "a process that won't die"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by a cup of tea on 2009-03-16
I'm using Transmission to download some torrents. It sorta stopped responding, and I can't kill the process. In System Monitor, I can click end process, and it gives me a warning, and when I click to end the process, it just....doesn't happen. 

A screenshot:
[http://img10.imageshack.us/img10/5610/transmissionl.png](http://img10.imageshack.us/img10/5610/transmissionl.png)

When I click the X on the top right of the blank Transmission window, I get a smaller box on top of it with another X. That smaller box is totally blank. 

I guess I'll try restarting my computer, but it seems odd that the process won't just die.

edit: oh hey, the process died. After like 20 minutes of fiddling around with screenshots of how it wouldn't die, and getting distracted, and all that. Weird that everything else on the computer was working normally during that time...

---

### Post by rafac24 on 2009-03-16
You can also type in the Terminal:

```
top
```

This will list the processes that are running. From there type the letter 'k' and the PID number (found to the left of each) to kill the process that may not be responding.

---

### Post by Gannon8 on 2009-03-16
Open a terminal. Type in:
```
killall -9 processname
```
and replace "processname" with whatever process is displayed in the system manager.

---

### Post by darkerlink on 2009-03-16
reminds me of the Simpsons episode where homer buys a computer and says "kill flanders..." LOL

But yeah, I would just open terminal and type


killall transmission

not sure what the -9 is for but usually that works just fine.

---

### Post by a cup of tea on 2009-03-16
Ok, thanks. :D

---

### Post by orethrius on 2009-03-16
> **darkerlink said:**
> reminds me of the Simpsons episode where homer buys a computer and says "kill flanders..." LOL

But yeah, I would just open terminal and type


killall transmission

not sure what the -9 is for but usually that works just fine.
15: SIGTERM: "This process stopped.  Kill it, but abort if errors occur."
9: SIGKILL: "This process won't die.  Ignore all commands to abort and kill it again."

:-D

---

### Post by a cup of tea on 2009-03-17
I think Firefox wants to eat my brain. :shock:

Today I had a zombie Firefox in System Monitor. screenshot:
[http://img23.imageshack.us/img23/2661/firefoxzombie2.png](http://img23.imageshack.us/img23/2661/firefoxzombie2.png)

Firefox was working when I saw this. What does it mean when Firefox is a zombie or uninterruptible? I'm used to Windows, where Firefox is either responding or not responding. Also, I stopped trying to use Transmission for torrents, because it kept going unresponsive on me every time I tried to edit my preferences.

---

### Post by raul_ on 2009-03-17
> **a cup of tea said:**
> I'm using Transmission to download some torrents. It sorta stopped responding, and I can't kill the process. In System Monitor, I can click end process, and it gives me a warning, and when I click to end the process, it just....doesn't happen. 

A screenshot:
[http://img10.imageshack.us/img10/5610/transmissionl.png](http://img10.imageshack.us/img10/5610/transmissionl.png)

When I click the X on the top right of the blank Transmission window, I get a smaller box on top of it with another X. That smaller box is totally blank. 

I guess I'll try restarting my computer, but it seems odd that the process won't just die.

edit: oh hey, the process died. After like 20 minutes of fiddling around with screenshots of how it wouldn't die, and getting distracted, and all that. Weird that everything else on the computer was working normally during that time...

Well, that's just how stable Linux is...processes won't  even die :popcorn:

---

### Post by SunnyRabbiera on 2009-03-17
try adding the kill application applet, I use it all the time.
right click a panel, select "add to panel"
Put the force quit applet into your panel

And when that doesnt work, hire a priest and shout "the power of Christ compels you, the power of Christ compels you!"*

*works in Christianity, for Islam its "the Power of Allah compels you"
for Judaism its "the power of Jehovah compels you"
For Hindu its "the power of Shiva compels you"
For Buddhism its "The power of Buddha compels you"
For Pastafarianism its "the power of the flying spaghetti monster compels you"
and so fourth...

---

### Post by raul_ on 2009-03-17
> **SunnyRabbiera said:**
> try adding the kill application applet, I use it all the time.
right click a panel, select "add to panel"
Put the force quit applet into your panel

And when that doesnt work, hire a priest and shout "the power of Christ compels you, the power of Christ compels you!"*

*works in Christianity, for Islam its "the Power of Allah compels you"
for Judaism its "the power of Jehovah compels you"
For Hindu its "the power of Shiva compels you"
For Buddhism its "The power of Buddha compels you"
For Pastafarianism its "the power of the flying spaghetti monster compels you"
and so fourth...

Or you could just run xkill. The thing is that xkill doesn't actually kill the process, I think. It just destroys the window. Or something like that...I'm saying that because if you xkill Firefox, it will complain that it's still running when you open it again. But Firefox is a strange beast

---

