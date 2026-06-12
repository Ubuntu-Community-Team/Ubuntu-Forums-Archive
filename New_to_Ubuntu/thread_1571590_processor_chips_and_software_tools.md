---
title: "processor chips and software tools"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by vinceCOOK on 2010-09-09
Hello Forum People,

i was just wondering how good Ubuntu is on Multi core chips?

I was a little confused about tools written with a "multi threaded" programming approach and tools written in "multi core" programming approach.

My chip is a single core "hyperthread" chip. Does this chip perform
best on a software tools that "single core" or "multi core" or "multi thread" programmed?.

Say for example Audacity music tool? is it "single core", "multi thread" or "multi core" programmed?

maybe my understanding is not so good.

The way i understood things was that tools written with the "multi core" programming approach perform good on single core hyperthread chips. (as compaired to just a single core chip)

it's out of interest that i am enquiring,

I assumed that Ubuntu itself is a "multi everything OS" so it
leverages hyperthreading as best it can?


thanks,

Vince.

---

### Post by lisati on 2010-09-10
My laptop has a dual-core CPU. Ubuntu 10.04 64-bit works well enough for my liking on it.

---

### Post by 3rdalbum on 2010-09-10
"Multithreaded" code is the same as "multicore" code. Some Linux programs are multithreaded, some are not (it depends on whether a task can be split up into more than one thread). You can always run two single-threaded programs on your Hyperthreaded processor.

---

