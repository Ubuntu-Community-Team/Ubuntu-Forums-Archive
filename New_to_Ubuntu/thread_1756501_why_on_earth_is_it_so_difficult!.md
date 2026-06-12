---
title: "why on earth is it so difficult?!"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by pacalici on 2011-05-12
all i wanna do is install gcc3.2 and i;m at the end of my patience here. after spending hours figuring out all this intricate linux-like stuff, i finally get to the part where i 'make bootstrap' to build gcc. but does it work? no, i get this error message:
/home/user/gcc32/gcc-3.2/gcc/read-rtl.c:662:8: error: lvalue required as increment operand.

what am i supposed to do, change the source files? 

i'd rather change my diploma subject than ever going back to this unusually user unfriendly os ever again.

---

### Post by snowpine on 2011-05-12
Welcome to the forums Pacalici!

It is actually incredibly easy to install gcc in Ubuntu. Simply search for it in the Software Center, or if you're a terminal guy,

```
sudo apt-get update && sudo apt-get install gcc
```

This will install the current gcc 4.5.2. (gcc 3.2 is very outdated)

---

### Post by old_codger on 2011-05-12
> **pacalici said:**
> all i wanna do is install gcc3.2 and i;m at the end of my patience here. after spending hours figuring out all this intricate linux-like stuff, i finally get to the part where i 'make bootstrap' to build gcc. but does it work? no, i get this error message:
/home/user/gcc32/gcc-3.2/gcc/read-rtl.c:662:8: error: lvalue required as increment operand.

what am i supposed to do, change the source files? 

i'd rather change my diploma subject than ever going back to this unusually user unfriendly os ever again.
Is there some reason you're using a gcc version that's years out of date as a matter of interest? That came out in about 2003-4 I believe.

I installed the current version by selecting 'Applications/Ubuntu Software Centre' and then entered 'gcc' in the search box at top right and clicking 'install'.

---

### Post by old_codger on 2011-05-12
> **snowpine said:**
> Welcome to the forums Pacalici!

It is actually incredibly easy to install gcc in Ubuntu. Simply search for it in the Software Center, or if you're a terminal guy,

```
sudo apt-get update && sudo apt-get install gcc
```

This will install the current gcc 4.5.2. (gcc 3.2 is very outdated)
If he's compiling stuff it might require a particular version I suppose as otherwise he might have to rewrite and if it's not his code it can get 'hairy'.

Dunno?!

---

### Post by Slim Odds on 2011-05-12
> **pacalici said:**
> ...

i'd rather change my diploma subject than ever going back to this unusually user unfriendly os ever again.

Sounds more like a personal problem than an unfriendly OS.

---

