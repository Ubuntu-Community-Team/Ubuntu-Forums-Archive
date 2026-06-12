---
title: "mencoder bash script"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by MrWES on 2009-09-06
I need help putting the following mencoder command into a script

```
mencoder movie.avi -sub movie.srt -subfont-autoscale 1 -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1800
```

I made a script called addsub and put $1 for the movie.avi; $2 for movie.srt and $3 for movie.hardsubs.avi. Unfortunately, that didn't work, and I think it was because some of my file names have spaces. Anyone willing to give this a shot?


Thanks,
Bill

---

### Post by unutbu on 2009-09-06
Try:
```

mencoder "$1" -sub "$2" -subfont-autoscale 1 -o "$3" -oac copy -ovc lavc -lavcopts vbitrate=1800
```

The double-quotes tell bash not to break apart the variable into more than one argument.

---

### Post by Penguin Guy on 2009-09-06
It would be very helpful if you could post your script (inside [php] tags please). It would also be very helpful if you could tell us what you are actually trying to achieve.

---

### Post by falconindy on 2009-09-06
> **Penguin Guy said:**
> It would be very helpful if you could post your script (inside [php] tags please). It would also be very helpful if you could tell us what you are actually trying to achieve.

What? It's clear he's trying to make a shortcut for an otherwise lengthy command. Unutbu has it right with putting the variables in quotes. Without the quotes, the program will think arguments with spaces are multiple arguments.

---

### Post by bear24rw on 2009-09-06
if you file names have spaces make sure you use \ before the space..

file name.avi
file\ name.avi

---

### Post by MrWES on 2009-09-06
> **unutbu said:**
> Try:
```

mencoder "$1" -sub "$2" -subfont-autoscale 1 -o "$3" -oac copy -ovc lavc -lavcopts vbitrate=1800
```

The double-quotes tell bash not to break apart the variable into more than one argument.

@unutbu; that was it -- I'm still learning bash scripting.


Thanks,

Bill

```
#!/bin/bash
mencoder "$1" -sub "$2" -subfont-autoscale 1 -o "$3" -oac copy -ovc lavc -lavcopts vbitrate=1800

```

---

