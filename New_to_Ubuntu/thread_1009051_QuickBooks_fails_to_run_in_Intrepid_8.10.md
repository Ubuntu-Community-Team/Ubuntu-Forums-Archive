---
title: "QuickBooks fails to run in Intrepid 8.10"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-12
I had QuickBooks running great in prior versions of Ubuntu - 8.04, 7.10, and 7.04.  But, it fails in 8.10.

I am using the same version of CodeWeavers Crossover 6.2

This is how Quick Books gets started:
sh exec "/opt/cxoffice/bin/wine" --bottle "win98" --check --wait-children
--start "c:/windows/profiles/crossover/Desktop/QuickBooks Enterprise
Solutions 4.0.lnk" "$@"

And this is the error:
wine: Unhandled page fault on read access to 0x00000000 at address
0x7e33b6d6 (thread 000e), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit
code (0x7e33b6d6).
Register dump:
.....


Anyone have any ideas?

Thanks

Carl

---

### Post by BentSlightly on 2008-12-31
Carl, 
Have you found resolution to this problem?

I  assume you were using Wine to run quickbooks, I am in the same position as you.

---

### Post by Kellemora on 2008-12-31
As far as I know, QuickBooks will not run in Wine or Crossover!

Some say it works in Virtual Box, but I couldn't get it to and everything I was told to try didn't help one iota either.

TTUL
Gary

---

### Post by cwmoser on 2009-01-01
I run QuickBooks Enterprise Solutions 4.0 via CrossOver on Ubuntu 8.04.

I found that Quick Books is sensitive to the amount of RAM you have.
Quick Books works great in 1GB or 2GB RAM.
Quick Books will not start if you have 3GB or 4GB RAM.

I know its odd.  In any case, with Ubuntu, you don't really have to have a lot RAM and when I run 2GB I've never seen it consume more than 700GB.

So, if you are having problems getting Quick Books to work, remove RAM - get it down to 2GB.

Carl

---

