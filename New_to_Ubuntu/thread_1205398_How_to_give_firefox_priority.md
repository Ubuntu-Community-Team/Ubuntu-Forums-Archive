---
title: "How to give firefox priority?"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by raccoonone on 2009-07-06
I keep having problems with Firefox, or other fairly lightweight GUI processes hanging when I'm doing something in the background like copying a file.
I read a couple guides, and tried "sudo ionice -c1 -p<firefox ID>" to give Firefox real time disk priority, and I tried "sudo renice -7 <firefox ID>" to increase the CPU time for Firefox. But neither of those worked.

Is there a way that I can give whatever application has focus priority over other things that are running?

---

### Post by lovinglinux on 2009-07-06
To give Firefox the highest priority, use this:

```
nice -n -20 firefox
```

Nevertheless, I would recommend the performance tips on the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I tried to use the priority command once. I knew it worked, because the system monitor applet shows the processor cycles used by nice, but I didn't make much difference in performance or responsiveness of Firefox.

---

