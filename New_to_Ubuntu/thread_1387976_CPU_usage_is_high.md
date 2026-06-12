---
title: "CPU usage is high"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Ghost Hacks on 2010-01-22
Does anyone know why my cpu usage is so high, even when I'm not using the PC its like at 70% usage normally.  I'm not using much ram but the CPU usage is a lot higher then Windows 7 or any Windows for that matter.  I think it might be because I don't have any video driver installed.

---

### Post by JiuJitsu500 on 2010-01-22
Yeah, I'd say get the updates and all your drivers squared away then check...

System monitor is a good tool to see what's up with the processes and to kill them, but a good one also to see what's misbehaving is Power Top:

sudo apt-get install powertop

and you can run it:

sudo powertop

and see what's happening a little better than the normal monitors :)

EDIT* should add it's just to check so you can make the changes in that program yourself and lower CPU and Ram usage, etc...

---

### Post by earthpigg on 2010-01-22
also be sure to check out htop.

sort by cpu% and see what the offending program(s) is or are.

let us know what it is, and we can advise from there.

---

### Post by Ghost Hacks on 2010-01-22
It's Firefox and Steam they refuse to sleep, as soon as they do they wake back up.  Not a big deal though, also I'm using 1GB of ram =O  But that's because Firefox and Steam again so not a big deal.

I closed the Friends List and my cpu dropped to 40% lol.

---

### Post by J V on 2010-01-22
Flash is porbably another 20/30%, close whatever FF pages have flash on them...

---

