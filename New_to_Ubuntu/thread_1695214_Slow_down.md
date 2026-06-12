---
title: "Slow down"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by detour21 on 2011-02-25
Since updating to v10, Ubuntu gradually slows to a crawl. I leave the machine on 24/7 as it is a web server and don't use it for much else. When I do go on after several days everything takes ages to respond, every function, open, close, single/double click, etc. The only way to get back up to speed is restarting. I have run the janitor (no help) and need any suggestions as to what to do to prevent this from happening, I update the system once a week so I think I am current. Help?

---

### Post by Ben Page on 2011-02-25
Try cleaning your cache and temp folders, old kernels and unneeded packages. Use Ubuntu Tweak for easy and safe cleaning. I would also look at frequency scaling when the machine slows down, it may be stuck on lower CPU frequency after idling for longer periods of time.

---

### Post by hansolo4949 on 2011-02-25
How much ram do you have? It sounds like the systems ram is filling up, and it's using it's swap file more frequently, which is a lot slower, since it's on the HDD. Any other thoughts?

---

### Post by tbone7 on 2011-02-26
I have the exact same symptoms. I thought it was related to a [memory leak]("http://ubuntuforums.org/showthread.php?t=1683248"), but now I'm not sure any more. Very strange and frustrating.

---

### Post by pi.boy.travis on 2011-02-26
You're using a desktop install as a full-time web server? The desktop kernel ist't optimized for that kind of workload. I'm guessing the scheduler is sucking up all your RAM. Install the Server Edition, that kernel is optimized for this kind of workload.

---

### Post by HermanAB on 2011-02-26
Sigh, so many blue sky suggestions and not a single attempt at finding out what is wrong...

First do this:
$ top

See what is chewing up your resources and kill it.  Then try to figure out why it is doing so and find a newer/older version of the culprit that works better.

---

### Post by tbone7 on 2011-02-26
I'm not running a server, I just had the symptoms. I have now cleaned the system fan and cleared every bit of dust to test if the problem was heat-related. So far after boot both CPU and GPU is approx. 5 degrees C lower in average. Will let you know if the problems disappear.

---

### Post by relay_man on 2011-02-26
I agree with HermanAB

"top" is a program that will tell you what processes are running, amount of memory/swap usage and cpu time that is being allocated for those processes, etc.

I prefer a similar utility that is called htop.  It is a fantastic tool
that can help you solve many problems.

You can install htop (or top) from terminal or using synaptic package manager.
Whatever you decide, if you are able to resolve your problem, please post again to let others know what you found.

---

