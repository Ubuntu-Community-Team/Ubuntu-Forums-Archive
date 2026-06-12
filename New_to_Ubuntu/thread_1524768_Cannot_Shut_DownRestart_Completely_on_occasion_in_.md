---
title: "Cannot Shut Down/Restart Completely on occasion in 10.04 Desktop."
date: 2010-07-05
forum: New to Ubuntu
---

### Post by kirbyparufo on 2010-07-05
About 10-25% of the time, while shutting down or restarting (through a button on my computer or a button on the top panel), my computer just hangs on the purple screen with "Ubuntu" and the loading bar, and I have to forcefully turn it off. Is there any way to solve this?

EDIT: I didn't have this problem before doing a complete reinstallation of Ubuntu 10.04, it this bit of info helps.

---

### Post by l3ij0u on 2010-07-06
Hi,
 
even I'm having the same problem. Sometimes, even a normal boot just hangs. Any help here appreciated.
 
Yes I'm pretty new to Ubuntu
 
Thanks,
Bijou.

---

### Post by nothingspecial on 2010-07-06
The first thing to try is shutting down from the terminal and see if there are any errors.

```
sudo shutdown -h now
```

---

### Post by kirbyparufo on 2010-07-06
> **nothingspecial said:**
> The first thing to try is shutting down from the terminal and see if there are any errors.

```
sudo shutdown -h now
```

I tried the code many times (around 6-10, can't remember) to get a good sample size for this "experiment" (;)), and I never got a single error, and the system usually shot down normally. However, on my latest attempt at entering the code, the system started the shutdown process, but hung on the Ubuntu screen as described in my first post (no errors though).

---

### Post by kirbyparufo on 2010-07-06
Any advice anybody?

---

### Post by kirbyparufo on 2010-07-07
If nobody can offer advice here, is there another subforum here I should turn to? :|

---

### Post by RedRat on 2010-07-07
> **kirbyparufo said:**
> I tried the code many times (around 6-10, can't remember) to get a good sample size for this "experiment" (;)), and I never got a single error, and the system usually shot down normally. However, on my latest attempt at entering the code, the system started the shutdown process, but hung on the Ubuntu screen as described in my first post (no errors though).
I had this problem too on my 10.04 laptop. The shutdown icon in the uppermost task bar, for reasons known only to Ubuntu, disappeared. I could get to the terminal and tried the command line shutdown. It did as you said, got partially through it and then stopped. the only way to shutdown was to physically hold the on/off button down for a few seconds. When I turned the machine back on after about 30seconds, I got fdsk running, not a complete scan but it took about a minute.

I don't like to shut the machine down by using the on/off button, so if someone has some ideas on this, would also appreciate it.

---

### Post by kirbyparufo on 2010-07-09
Can anybody help with this issue? Or is this purely related to the hardware (ie, something that can't be fixed)? :(

---

### Post by kirbyparufo on 2010-07-12
I guess I'll bump this one more time and ask in another forum if a reply isn't made. :?

---

### Post by S.R on 2010-07-12
Wonder if you a have a process hanging?

---

### Post by kirbyparufo on 2010-07-12
Well, I have nothing running visibly while shutting down.

---

### Post by nothingspecial on 2010-07-12
Sorry I haven`t got back to you.

When I said shut it down from the terminal, what I should have said, is console or tty(1-6)

Press Ctrl Alt F1 then do ```
sudo shutdown -h now
```

If you just do it from a terminal in the gui you are not going to see any errors, my fault.

---

### Post by kirbyparufo on 2010-07-13
Using the console, I got no errors. I attempted shutting down that way about 5 times, but each time I shut down the machine did as commanded (if I tried enough, I guess I might get it to hang again, should I do so?). A bunch of text appeared each time I entered the code, but the screen snaps off too quickly to read what was written.

---

### Post by karolosz on 2011-04-04
no solutions at all?? I installed 10.04 long time ago, troubles appear about 2 months ago...???

---

