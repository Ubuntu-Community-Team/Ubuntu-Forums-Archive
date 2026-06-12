---
title: "Nvidia seems too slow"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-02-21
I'm running Ubuntu 9.10 with the Nvidia drivers (version 96) installed.

Any sort of games, including relatively simple games like TeeWars or Kobo Delux use up all of my CPU and slow the computer down to a crawl.

This isn't the newest computer in the world, but I certainly think it should be fast enough to run these games.

One thing I noticed is that there is no write-combining line in proc/mtrr:
```
$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x01ff80000 (  511MB), size=  512KB, count=1: uncachable

```

On my other computer, with an intel graphics card, I also had this problem and adding the write-combining line manually really sped things up.

Does anyone know if this could be a similar problem?  Do I need to add the write-combining line myself?  If so, does anyone have instructions on how to figure out what that line would be?  

Or is this a completely different issue?

Thanks for your help.

---

### Post by philinux on 2010-02-21
> **stoogiebuncho said:**
> I'm running Ubuntu 9.10 with the Nvidia drivers (version 96) installed.

Any sort of games, including relatively simple games like TeeWars or Kobo Delux use up all of my CPU and slow the computer down to a crawl.

This isn't the newest computer in the world, but I certainly think it should be fast enough to run these games.

One thing I noticed is that there is no write-combining line in proc/mtrr:
```
$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=  512MB, count=1: write-back
reg01: base=0x01ff80000 (  511MB), size=  512KB, count=1: uncachable

```

On my other computer, with an intel graphics card, I also had this problem and adding the write-combining line manually really sped things up.

Does anyone know if this could be a similar problem?  Do I need to add the write-combining line myself?  If so, does anyone have instructions on how to figure out what that line would be?  

Or is this a completely different issue?

Thanks for your help.

Does turning off compiz make any difference?

---

### Post by stoogiebuncho on 2010-02-21
No, it doesn't really make a difference.

Maybe the games just aren't very efficient?  I just tried World of Goo and it works great and only uses 15-17% of the CPU.

---

