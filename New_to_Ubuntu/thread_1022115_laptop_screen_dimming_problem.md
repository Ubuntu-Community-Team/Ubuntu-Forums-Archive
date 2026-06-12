---
title: "laptop screen dimming problem"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jleewach on 2008-12-26
Hi all,

I have kind of a strange problem. I'm running Ubuntu 8.04 on my Acer Extensa 4420 notebook, and it works great, except a slight problem I'm having w/ the screen brightness. When plugged into power, I have the screen set at full brightness, but if left idle or unplugged, the screen dims (which is perfectly fine & what I want to happen), however the problem is, once I plug it back in or bring it out of idle, the brightness goes back up, but not all the way to the original full brightness. It's always a bit dimmer. It's not a huge issue, but what I find happening is that, if I idle several times in a session, the screen eventually get's very dim from the incremental dimming of coming out of idle. Of course, I can always increase the brightness back up using the fn+ arrow key, but is there a way to keep the screen at full brightness when not in idle or plugged in? It's just kind of annoying to have to keep brightening the screen. Any help would be appreciated.

---

### Post by crazyness003 on 2008-12-26
Thats weird. Anyway, the only help i can give is this: The Power Management  Preferences control your screen brightness. You can access it thru System-> Preferences -> Power Management and see if you have anything there that will tweak. Other than that, this sounds like a bug, and i wouldn't hesitate to report it on Launchpad.net
Other than that, i dont know. sorry.

Anyway, welcome aboard.
btw: Which part of Illinois you from? (optional answer) :D

---

### Post by sportscrazed2 on 2008-12-26
> **jleewach said:**
> Hi all,

I have kind of a strange problem. I'm running Ubuntu 8.04 on my Acer Extensa 4420 notebook, and it works great, except a slight problem I'm having w/ the screen brightness. When plugged into power, I have the screen set at full brightness, but if left idle or unplugged, the screen dims (which is perfectly fine & what I want to happen), however the problem is, once I plug it back in or bring it out of idle, the brightness goes back up, but not all the way to the original full brightness. It's always a bit dimmer. It's not a huge issue, but what I find happening is that, if I idle several times in a session, the screen eventually get's very dim from the incremental dimming of coming out of idle. Of course, I can always increase the brightness back up using the fn+ arrow key, but is there a way to keep the screen at full brightness when not in idle or plugged in? It's just kind of annoying to have to keep brightening the screen. Any help would be appreciated. i think it's a power saving measure i wouldn't worry about it try going to system>preferences>power management and under the on battery power tab try unchecking reduce backlit brighness, and dim display when idle

---

### Post by crazyness003 on 2008-12-26
he knows about that, but every-time he resumes from idle, his display only lights up (example) 99%. So after (a theoretical) 99 resumes from idle, his display will be 99% of 99% of 99% of 99%.....of 99% = 1% SCREEN BRIGHTNESS!

Id report this as a bug, this will ensire that someone sees it, and if it has been encountered before, there may be a fix.
Go to [Launchpad.net](https://launchpad.net/ubuntu/+filebug/+login), register (its free) and report the bug in the ubuntu section.

---

### Post by sportscrazed2 on 2008-12-26
> **crazyness003 said:**
> he knows about that, but every-time he resumes from idle, his display only lights up (example) 99%. So after (a theoretical) 99 resumes from idle, his display will be 99% of 99% of 99% of 99%.....of 99% = 1% SCREEN BRIGHTNESS!

Id report this as a bug, this will ensire that someone sees it, and if it has been encountered before, there may be a fix.
Go to [Launchpad.net](https://launchpad.net/ubuntu/+filebug/+login), register (its free) and report the bug in the ubuntu section.

my bad got to read entire posts before posting

---

### Post by jleewach on 2008-12-26
I'll definately report if the case that this is a bug. I just didnt know if anyone else has been having the problem.

And to answer your question, I'm from Southern Illinois (near St. Louis, MO)

Thanks!

---

### Post by crazyness003 on 2008-12-26
No problem. 

I did give it a little more though, and maybe its just a qwirk. Try disabling the "idle" feature and re-enabling it, see what happens. 
Also, have you done any major updating recently? If so, its wise to do a restart (im talking about high-priority updates, with libs and modules an'such).

When you do report the bug (if you do, and i hope you do) make sure you have a link to there from here (and vice-versa).
As lame as that may sound, if someone else has a similar problem, they can quickly find discussions on launchpad to help with solving the problem.

Also, for better search purposes, its also recommended (not required) to add tags to your threads. It just helps with search tools better.

I sound like im pestering you, if so, sorry.
Im originaly from Northern Illinois (far Chicago suburbs) and have lived in Rockford. Thats the only reason why I asked.

---

### Post by Ripfox on 2009-01-18
Same problem with an Acer 5315-2153

---

### Post by Canobuntu on 2009-02-21
I have the same problem with a Dell Inspiron 1525n. After dimming for Power Save, it only returns to about 85% brightness.

---

### Post by Kellemora on 2009-02-21
Hi JLee

I don't have a laptop, but we do have a few computers with LCD screens that gave us a similar problem.  If they go to sleep they didn't go to full brightness, but this was not all the time, only if it was over 45 minutes or closer to an hour.

I stumbled on what was causing it on our screens anyhow by setting the screensaver sleep setting over 2 hours and the screens still went to sleep anyhow.

So I searched around and found a Power Save setting that was set to 40 minutes to put screen to sleep under System/PowerManagement/Display.

Apparently this timer runs regardless of how your screensaver is set.

If I set the screensaver controls to go into screensaver mode in 5 minutes and put the monitor to sleep in 30 minutes, if we would bring the monitor up before the 40 minute timer kicked in, we did not have the dimming problem.  BUT, if we waited longer than 40 minutes, then we had the dimming problem.  On a computer that's only used like once every other hour, by the end of the day, one would think the monitor died.
We just set the display control to NEVER and that solved our problem!
The screensaver programs turn of monitor still works and does not cause that problem with the dim screen upon wakeup.

Worth a try on your laptop!

TTUL
Gary

---

