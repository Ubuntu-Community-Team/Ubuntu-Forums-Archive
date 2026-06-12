---
title: "Incompatibility with AMD 64 X2 ????"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-17
I think I have found an incompatibility or bug associated with the AMD 64 X2 processor.  It appears to be either Ubuntu or Codeweavers Cross Over product, or in Wine but there are so many variables I need more data.  What I do know is that there is something that is preventing QuickBooks from running.  Here is what I have found:

Intel PC:  P4 3Ghz, 2GB RAM, Ubuntu 8.04, Codeweavers 6.2, Wine 1.0
QuickBooks 4.0 runs great under Codeweavers. 
Quicken 2005 runs great under Codeweavers.
eSword, Spider Solitaire runs great under Wine.


AMD PC:  AMD 64 X2 6000+, 4GB RAM, Ubuntu 8.04, Codeweavers 6.2, Wine 1.0.
QuickBooks 4.0 will not run.
Quicken 2005 runs great
eSword, Spider Solitaire runs great under Wine.


On the AMD PC, I have tried both Codeweavers 6.2 and 7.2.
On the AMD PC, I have tried to get QuickBooks to run by:
- installing both Ubuntu 8.04 and 8.10
- installing both versions of Codeweavers
- I cloned the hard drive from the Intel PC and it booted and ran on the AMD PC but QuickBooks would not run

When I say QuickBooks will not run, I mean that it presents a small window with a yellow "!" caution icon and an OK button.  After clicking the OK button 9 times, this message appears:  [B]QuickBooks requires 2.5 Megabytes (2560K) of free RAM.  Close other applications in order to free up memory. 
[/B]
So, what do you think?  Is is a quirk with the AMD 64?  A quirk with Ubuntu as it runs on the AMD 64?  A Codeweavers quirk?  Could it be some esoteric feature in Quick Books that ties it to something with Intel processors?

Comments?


Thanks

Carl

---

### Post by talsemgeest on 2008-12-18
I would think it would just be an incompatibility between QuickBooks and Windows emulators. I'm guessing it looks somewhere for how much RAM is available, but Codeweavers doesn't emulate that function.

---

### Post by cwmoser on 2008-12-27
I think I have some insight with the QuickBooks problem.

When I had 4GB RAM, QuickBooks would not start up.
When I backed the RAM down to 2GB, QuickBooks would start.
When I installed 3GB RAM, QuickBooks would not start up.

Looks like QuickBooks v4.0 wants no more than 2GB RAM installed.


Carl

---

