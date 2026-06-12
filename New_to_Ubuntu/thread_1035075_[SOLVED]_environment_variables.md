---
title: "[SOLVED] environment variables"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Jackissimus on 2009-01-09
Hi!

I need to set up some environment variables for my project in college. I have this script, that is supposed to set those variables, but it doesn't work. The script looks like this:

```
#! /bin/sh
export IPPROOT=/opt/intel/Compiler/11.0/074/ipp/em64t
export INCLUDE=$IPPROOT/include:$INCLUDE
export LD_LIBRARY_PATH=$IPPROOT/sharedlib:$LD_LIBRARY_PATH
export LIB=$IPPROOT/lib:$LIB
export CPATH=$IPPROOT/include:$CPATH
export LIBRARY_PATH=$IPPROOT/lib:$LIBRARY_PATH
export NLSPATH=$IPPROOT/lib/locale/%l_%t/%N:$NLSPATH
```

I run the script like this - ./script.sh
Then I check 'env' and 'export' and the variables are nowhere to be found. So I type manually into bash 'export IPPROOT=/opt/intel/Compiler/11.0/074/ipp/em64t'. Then I check 'env' and 'export' and voila, the variable is there. What am I doing wrong? I know this is really simple for you guys, so please help me out :)

---

### Post by jken146 on 2009-01-09
Try !#/bin/bash rather than sh.

---

### Post by Jackissimus on 2009-01-09
> **jken146 said:**
> Try !#/bin/bash rather than sh.
Nope, didn't work. Another suggestions?

---

### Post by sisco311 on 2009-01-09
> **Jackissimus said:**
> Nope, didn't work. Another suggestions?

use the source command to load the variables:
```
source ./script.sh
```
or
```
. ./script.sh
```

[http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html")

---

### Post by Jackissimus on 2009-01-09
> **sisco311 said:**
> use the source command to load the variables:
```
source ./1
```
or
```
. ./1
```

[http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html")

So cool! You just made one guy in the world very happy :)

---

### Post by sisco311 on 2009-01-09
Cool!

Please mark the thread **[SOLVED]** by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

Marking threads as **[SOLVED]**, after a solution has been found will help
others to find an expedient solution for their own issues.

---

