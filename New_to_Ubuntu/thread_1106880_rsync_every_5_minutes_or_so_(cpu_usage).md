---
title: "rsync every 5 minutes or so (cpu usage)"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by tdrusk on 2009-03-26
I want to run rsync every 5 minutes. If I create a script with a for loop that runs every 5 minutes will my computer eventually become slow? I know when I have an infinite loop with Java or C++ my system resources get used a lot. Will this happen with a script?

---

### Post by MrWES on 2009-03-26
> **tdrusk said:**
> I want to run rsync every 5 minutes. If I create a script with a for loop that runs every 5 minutes will my computer eventually become slow? I know when I have an infinite loop with Java or C++ my system resources get used a lot. Will this happen with a script?


You could run it in cron:

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /path/to/script


Bill

---

### Post by freak42 on 2009-03-26
+1 for cron.. (that's what it's here for)

if you really want to do it with a script, you might want to look at the sleep command (sleep), if you sleep your script within the loop for the 5 minutes it won't use much system resources:

something like:

loop (true) {
   sleep 300
   rsync mystuff
}


hth

---

### Post by tdrusk on 2009-03-26
[This]("http://www.howtoforge.com/mirror-your-web-site-with-rsync-on-fedora-10-p2") site tells me how to do it, but I don't really understand what it is doing. 

Can someone please tell me, or link to something that tells me, how to do it?

---

