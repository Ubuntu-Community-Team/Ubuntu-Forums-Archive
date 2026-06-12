---
title: "Kernel bug prevents shutdown of Ubuntu 9.04"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by meindian523 on 2009-05-26
My computer was booting,shutting down and rebooting normally enough upto the past few days before I had a kernel bug occur and prevent shutdown with a long list of hex numbers and services open at the time.Relevant part of the error:
```

[107.616395]------------[ cut here ]---------------------------
[107.616448]kernel BUG at /build/buildd/linux-2.6.28/arch/x86/mm/pat.c: 298!
[107.616494]invalid opcode: 0000 [#1] SMP

```
Similar issue [here]("http://translate.google.com/translate?prev=hp&hl=en&js=n&u=http%3A%2F%2F74.125.153.132%2Fsearch%3Fq%3Dcache%3AeMXDCT4baqAJ%3Awww.ubuntu-es.org%2F%253Fq%253Dnode%2F116044%2Bkernel%2BBUG%2Bat%2B%2Fbuild%2Fbuildd%2Flinux-2.6.28%2Farch%2Fx86%2Fmm%2Fpat.c%3A%2B298%26cd%3D1%26hl%3Den%26ct%3Dclnk%26gl%3Din%26client%3Dfirefox-a&sl=es&tl=en&history_state0="),only the latest open file changes from (attempted) shutdown to (attempted) shutdown,and my processor is Pentium D (2.80GHz).Same motherboard(D101GGC),no external graphics,internal graphics ATi Radeon XPRESS 200,512MB DDR1 RAM,and running 64 bit 9.04.What confuses me is that the path shows arch as x86 while I'm running x86_64 :confused:

I'm presently shutting down using the emergency sequence Alt+SysRQ+RSEIUO
TIA for any and all help.

---

### Post by meindian523 on 2009-05-27
bump

---

### Post by lisati on 2009-05-27
Are any of the [bugs]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=kernel+invalid+opcode+0000&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") here relevant? One or two seem similar

---

### Post by meindian523 on 2009-05-27
Didn't see any of them concerning pat.c,which is the file my bug points to.And I posted so I could ask for a workaround.

edit:Also,this bug occurred just a few days ago,the same kernel shutdown,restarted,etc nicely upto a few days ago.

---

### Post by meindian523 on 2009-05-29
bump.workarounds?

---

