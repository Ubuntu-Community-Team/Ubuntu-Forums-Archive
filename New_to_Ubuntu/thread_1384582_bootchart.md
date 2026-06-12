---
title: "bootchart"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by DestructionsRightHand on 2010-01-18
after installing bootchart and rebooting twice i find something must to wrong

output:
```

Parsing /var/log/bootchart
Jan 18, 2010 3:37:58 PM org.bootchart.Main render
WARNING: Unknown log file: Dominion-karmic-20100118-1.png
Jan 18, 2010 3:37:58 PM org.bootchart.Main render
WARNING: Unknown log file: Dominion-karmic-20100118-1.tgz
Jan 18, 2010 3:37:58 PM org.bootchart.Main render
WARNING: Unknown log file: Dominion-karmic-20100118-2.png
Jan 18, 2010 3:37:58 PM org.bootchart.Main render
WARNING: Unknown log file: Dominion-karmic-20100118-2.tgz
Jan 18, 2010 3:37:58 PM org.bootchart.Main render
WARNING: No process samples
Wrote image: ./bootchart.png

```

---

### Post by philinux on 2010-01-18
Not sure whats happening there. You're not trying to run it from a terminal are you.

It runs in the background at boot, then look in /var/log/bootchart for the output.

Did you install it from the repos via synaptic?

---

### Post by DestructionsRightHand on 2010-01-19
yes to running it from the bash and i installed it from bash with aptitude

---

