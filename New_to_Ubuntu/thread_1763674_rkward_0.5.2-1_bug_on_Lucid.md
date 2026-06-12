---
title: "rkward 0.5.2-1 bug on Lucid??"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by NoWayBack on 2011-05-20
Hi there,
I have been using rkward without trouble for sometime on R 2.11 (Lucid 10.04, Wubi on Windows XPSP3).  Last night I upgraded packages, which I've been avoiding for sometime and found I now have R 2.13.  rkward is 0.5.2-1 (not sure what it was before but suspect it was the same).  

R works fine from command line, but crashes whenever run in the rkward console for the most simple tasks, (like x=1) with the following error:


Error: unprotect(): only 1 protected items

 *** caught segfault ***
address (nil), cause 'memory not mapped'

Possible actions:
1: abort (with core dump, if enabled)
2: normal R exit
3: exit R without saving workspace
4: exit R saving workspace)

I have tried different versions of rkward (I think there initially was a  0.5.3-1installed) uninstalled and reinstalled via Synaptic, tried   0.5.5 from .tar - which couldn't do! and haven't been able to find people with similar issues on the web.

Do any more experienced users have any idea what's going on and how to fix this??

Thanks

NWB

---

### Post by NoWayBack on 2011-05-21
This seems to be a conflict between R 2.13.0 and rkward.  I reinstalled R 2.10 via Synaptic and it works OK.  Annoying though.  I wonder has anyone else had this experience?

Also I couldn't freeze the R version to 2.12.1 or 2.12.2. and 2.11 (my preferred) was not available on Synaptic - does anyone know why?  

And why would installing 2.11 from tar.gz be so difficult  - './configure' seemed to work but 'make' did not ('make: *** No rule to make target').  From what I can read on web it could be ./configure not making a make file, what do I look for to see if this is true?  Although I'm to scared to change anything now....

---

