---
title: "[SOLVED] I'm losing CPU cycles to &amp;quot;something&amp;quot;!!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Kareeser on 2008-12-06
Hey everybody,

So I'm using my laptop... sometimes I use xrandr to output it to my TV... good for movies and such.

Suddenly, my CPU usage rockets to 100% and stays there...

Now with Windows, I'd Ctrl-Alt-Del it, and check the processes, and shut down the offending process.

However, with Ubuntu, in the System Monitor, I can't see what's hogging all of my resources! The CPU graph shows 100% usage, but when I click the processes tab, nothing shows up using more than ~20%...

What's hogging my processor, and why can't I find it? :(

---

### Post by lukjad on 2008-12-06
When you are using your laptop, does it being at 100% give you any noticeable lag? Also, are you seeing this because you have the system monitor open? I am not sure of right now, but I did hear a while back that there was a memory leak in the system monitor. Could you get rid of the monitor for a while and see if the problem goes away?

---

### Post by john.hall on 2008-12-06
You might also try top if you think the system monitor is the problem.

---

### Post by Duck2006 on 2008-12-06
Also

cat /proc/meminfo

May help.

---

### Post by scorp123 on 2008-12-06
> **Kareeser said:**
> However, with Ubuntu, in the System Monitor, I can't see what's hogging all of my resources! That program itself is a resource hog.

Try running "top" inside a terminal ..... or "htop" (sudo apt-get install htop): "htop" has far nicer and coloured output. But both "top" and "htop" use way less resources than "System Monitor".

---

### Post by Kareeser on 2008-12-07
Cheers to all who replied.

There's no noticible lag, the laptop fan just starts spinning at 100%, which usually means the processor is at full speed (and not dialing down to 600 MHz from 1800 MHz, like normal).

Thought it might've been a bug, until I checked the CPU usage. I'll give the terminal command a shot.

Thanks!

Edit: heh heh... htop looks nice... almost too nerdy for me, but it gets the job done.

---

### Post by scorp123 on 2008-12-07
> **Kareeser said:**
>  heh heh... htop looks nice... almost too nerdy for me Talking of "nerdy": make a transparent terminal window e.g. via "compiz" and have it run semi-transparently over your desktop wallpaper ... ;)

---

### Post by Duck2006 on 2008-12-07
You don't need compiz to make the terminal window transparent.
Open the terminal click on edit then profile preferences then click on background then click transparent background and ajust it from there.

Or open the terminal and right click on the terminal window and goto profiles then click on profiles preferences.

---

