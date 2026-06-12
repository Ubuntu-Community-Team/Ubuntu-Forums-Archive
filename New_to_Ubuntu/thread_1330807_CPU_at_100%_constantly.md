---
title: "CPU at 100% constantly"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Daniel1994 on 2009-11-18
I'm running ubuntu 9.10 on an acer aspire 5738ZG, which is a pretty "strong" computer, but I am experiencing both short freezes and lags. I checked the system monitor, which says both CPUs are running on between 98% an 100% constantly.

I've run ubuntu an older acer aspire too, it worked great, and this computer have been running good too, until recently.

Does anybody have any idea what my problem are?

---

### Post by OffAxis on 2009-11-18
check out what processes are taking up the CPU time.

After initial install 9.10 (and maybe 9.04, I can't quite remember) builds an index of files. This process pegs the processor at nearly 100% until it completes, and I'm not aware of any feedback mechanism from that process.
If that's what's doing it, it'll finish eventually.

---

### Post by jmszr on 2009-11-18
Daniel1994,

You can run "top" in the terminal to see what is keeping your CPU occupied.

Or you can install "htop" if you prefer a GUI.

---

### Post by efflandt on 2009-11-18
Under System, Preferences, Appearance, see if disabling "Visual Effects" helps.

At the moment I am running Jaunty on an old PIII 550 w/320 MB RAM displayed on 27" HDTV w/Linksys WUSB56GSC wireless.  No speed demon, but works reasonably well since I bumped it up from 256 MB.

top - 18:20:58 up 50 min,  3 users,  load average: 0.07, 0.31, 0.64
Tasks: 106 total,   1 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.0%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    315404k total,   305588k used,     9816k free,    60476k buffers
Swap:  2353512k total,    83976k used,  2269536k free,   103744k cached

---

### Post by Daniel1994 on 2009-11-19
Thanks for your replies,

I've been using 9.10 since it came out, so I believe the indexing part is finished.

Turned off the effects yesterday, my cpu is back to normal now, so that might have been it.

I'm going to try turning the effects back on, to see if it happens again.

---

### Post by Daniel1994 on 2009-11-23
Believe it or not, but it was gnome-do that was causing the problems. Always thought gnome-do was a very light program, but well...

It doesn't always behave like this, for example now I am running Do without any issues.

---

### Post by fromthehill on 2009-11-23
had the same problem
just installed gnome-do to see what it did
I figured it had something to do with indexing but I like to be able to move the cursor when I have work to do:p

at least you don't need to worry about gnome-do not making efficient use of all your cpu-cores :D

---

### Post by wolfganggold on 2009-11-23
> Believe it or not, but it was gnome-do that was causing the problems.

Oh, I believe it! :)  I used gnome-do briefly but then stopped when I started to notice the same type of processor utilization shenanigans.  I switched to Avant Window Navigator and it's better.

---

