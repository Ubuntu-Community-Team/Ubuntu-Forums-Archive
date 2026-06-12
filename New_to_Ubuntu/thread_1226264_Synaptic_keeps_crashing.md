---
title: "Synaptic keeps crashing"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-07-29
I got a new computer today and I did a fresh install of Jaunty from a CD I got from Canonical. The install went smoothly and I did the systems first updates and I rebooted as requested by the update notifier. 

Problem is now whenever I open Synaptic it crashes and closely right after I open it. 

When I ran sudo update it looks normal but look what happens when I try to install the updates. 

```
gary@gary-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%
gary@gary-laptop:~$
```

I have never seen Ubuntu do this before and I'm at a loss at what to do.

---

### Post by Bigtime_Scrub on 2009-07-29
Nevermind. I had a problem with my sources.list. I guess me staying up all night makes me miss obvious things. Please disregard. I solved it.

---

