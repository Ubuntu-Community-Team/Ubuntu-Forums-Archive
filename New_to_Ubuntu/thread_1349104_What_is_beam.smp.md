---
title: "What is beam.smp?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by donato roque on 2009-12-07
I have my terminal up and was monitoring processes through htop and I saw something new-beam.smp.  I googled it and followed threads in launchpad and in this forum but I just can't get what this process do.  Beam.smp is very busy so far.  

    What does beam.smp do?

---

### Post by ikt on 2009-12-08
> **donato roque said:**
> I have my terminal up and was monitoring processes through htop and I saw something new-beam.smp.  I googled it and followed threads in launchpad and in this forum but I just can't get what this process do.  Beam.smp is very busy so far.  

What does beam.smp do?

I'm guessing you're running an application that uses couchdb, and beam.smp is apart of it.

What it does, I'm not 100% sure.

---

### Post by donato roque on 2009-12-11
> **ikt said:**
> I'm guessing you're running an application that uses couchdb, and beam.smp is apart of it.

What it does, I'm not 100% sure.

Thank you.

---

### Post by Neva on 2010-10-23
There's a thread on reducing beam.smp's cpu and memory usage here:
[http://ubuntuforums.org/showthread.php?t=1584326](http://ubuntuforums.org/showthread.php?t=1584326)

[QUOTE=Pernig]To fix, go to System > Preferences > Broadcast Preferences. Untick  'start service at login'. Restart computer. The process beam.smp is now  only using 10.3MB of memory at startup on my system.[/QUOTE]

Seems that gwibber's use of couchdb needs tweaking. Saw in the bug report that this was fixed in Ubuntu 10.10 due to switching to another database.

---

### Post by fabio.hipolito on 2011-03-03
Sorry this is solved. I have tried what was proposed and continued to have the same result.

Best regards.

---

