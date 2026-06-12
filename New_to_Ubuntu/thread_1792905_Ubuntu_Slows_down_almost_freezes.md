---
title: "Ubuntu Slows down almost freezes"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Go7enKs on 2011-06-28
Hey all, I just installed Ubuntu on my new Vaio S a few days ago. Worked smoothly till today. I installed a few updates (which I think might be the cause for the problem) and all of a sudden the system is super-slow, it almost freezes. Basically, it's unusable. Also, when I click on the icons on the top right hand, like the shutdown icon, sometimes instead of the normal menu, a white-colored blank menu comes up. 

How do I solve this problem?

---

### Post by jtarin on 2011-06-29
You need to give us some more information about your system....most of us don't have your model of Vao or a Vao at all for that fact.....and as to version of Ubuntu your using....how many post do I get before I'm considered a disqualified guesser?

---

### Post by Go7enKs on 2011-06-29
Sorry, I have Ubuntu 11.04

My laptop is a Sony Vaio VPCSB and recently (before the problem arose) I also did this:

> 2) Upgrade to the latest kernel using the kernel ppa ([https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)). Plenty of general sandybridge updates happening, and I feel its best to keep up with the latest while this hardware is still receiving a fair amount of developer attention.

3) Add the xorg-edgers ppa ([http://www.ubuntuupdates.org/ppas/87](http://www.ubuntuupdates.org/ppas/87)). There have been significant updates for sandybridge graphics recently, ones which probably won't find their way into the mainline repos until 11.10. I haven't experienced any system instability using this ppa, and overall my Unity experience is very smooth now.


Then yesterday I did an update (don't remeber what I updated because there were like 29 updates) and the problem started to occur.

---

### Post by amjjawad on 2011-06-30
I've been checking the forum for the last two days and I've seen a lot of threads similar to this one.

When you're at the login screen, try to login to GNOME Classic or GNONE with no effect. Will the same problem occur again?

I'm having problems with Unity so I'm avoiding using it and I'm using GNOME with no effect. It works okay but yes, it's slow ... much slower than Ubuntu 10.04.

---

### Post by wildmanne39 on 2011-06-30
> **Go7enKs said:**
> Sorry, I have Ubuntu 11.04

My laptop is a Sony Vaio VPCSB and recently (before the problem arose) I also did this:



Then yesterday I did an update (don't remeber what I updated because there were like 29 updates) and the problem started to occur.Hi, it is possible it is the updated graphics driver, new drivers tend to cause problems, it would be best not to update to bleeding edge packages or drivers because they can have a negative impact on your system. You should also check in synaptic and make sure you do not have prerelease or backport updates allowed, they can cause issues. Also there is a common problem that can be fixed by going to this link.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow) 
However I do not know that it will help in your case but you can try it.

---

