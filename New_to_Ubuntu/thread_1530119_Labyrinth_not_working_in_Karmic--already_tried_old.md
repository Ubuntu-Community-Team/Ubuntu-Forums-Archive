---
title: "Labyrinth not working in Karmic--already tried older v. of Python"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by bytescribe on 2010-07-13
I have something of a problem..

I want to use Labyrinth, the mind-mapping tool, but it crashes in Karmic. My boyfriend told me to download an older version of Python (v. 2.5) which is what Ibex included--and that was the last stable distro on which my bf was able to run Labyrinth. He was able to download the aforementioned older version of Python in Karmic and it worked fine...so I am not sure what's going on...do I need to go even older, like 2.4?

I researched bug reports for this specific problem, and I got the hint to try and launch Labyrinth from the terminal and here is what I got: 

[B]Traceback (most recent call last):
  File "/usr/bin/labyrinth", line 45, in <module>
    import utils
ImportError: No module named utils[/B]

The first message in the bug report I read said something about "no module named numeric"--at least that's what the first message in the report said...then came confirmed issues with Labyrinth in Jaunty and Karmic (which I am currently using) and now "nominated" for Lucid as of November of 2009. 

Here is [the link]("https://bugs.launchpad.net/ubuntu/+source/labyrinth/+bug/327174") to the report if anyone wants to get a better picture.

Anyhow...since MY terminal output said something about "no module named utils" but someone else's said "no module named numeric," I am unsure what I need to do...install numeric or utils or both...:confused:

Anyone got Karmic and using Labyrinth successfully? If so, what did you end up doing that might help me?

Thanks in advance for any workarounds you suggest! :D

---

### Post by bytescribe on 2010-07-13
Woo-hoo! Consider my problem solved...

What I discovered was:

1)I had not actually downloaded Python v 2.5 the first time round...I had only downloaded the documentation. :p

2)Once I downloaded the actual older version of Python, I ran the launch command through the terminal and got the same "no module named numeric" message those other people in the bug-report got. Soooo...

3)I downloaded python-numeric as suggested in the report and....

Bada-bing, bada-boom! Instant Labyrinth happiness! I can now use Labyrinth! \\:D/

:guitar: :guitar: :guitar: \\:D/  \\:D/ \\:D/

---

