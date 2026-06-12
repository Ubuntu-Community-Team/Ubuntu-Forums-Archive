---
title: "Elisa media centre not working after jaunty downgrade."
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Yvan300 on 2009-05-20
Ok everyone, i upgraded to jaunty and found that elisa did not work at all. So i decided to return back to ibex and now elisa does not work. 

P.S it worked in ibex flawlessly before the jaunty upgrade.

Here us what i get when i try to run it from a terminal.

Traceback (most recent call last):
  File "/usr/bin/elisa", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 2566, in <module>
    parse_requirements(__requires__), Environment()
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 524, in resolve
    raise DistributionNotFound(req)  # XXX put more info here
pkg_resources.DistributionNotFound: elisa==0.5.35

Hope it helps, bye :)

---

### Post by MontelEdwards on 2009-05-20
yo Yvan300, did you just update your sources or did you do a real downgrade? Because it looks like Elisa dosent know your distro. I would reccomend installing ibex clean, and backing up.

---

### Post by Yvan300 on 2009-05-20
Actually i did do a clean install but i didin't not reformat my home partition, maybe that's the problem.

---

