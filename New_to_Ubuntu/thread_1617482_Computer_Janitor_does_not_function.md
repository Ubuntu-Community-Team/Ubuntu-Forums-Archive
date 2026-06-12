---
title: "Computer Janitor does not function"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by phubert28 on 2010-11-09
64 bit Ubuntu 10.10, upgraded from 10.4


when I try to run Computer Janitor, I get the following pop-up message:

"System clean up could not complete. Be sure no other package manager such as Synaptic or Update Manager is running."

This happens even at startup, before I've RUN anything!

My Update Manager also will not Install Updates.

Is there a way to run Computer Janitor from Terminal????

---

### Post by LowSky on 2010-11-09
terminal command for cleaning up is

sudo apt-get autoremove

---

### Post by phubert28 on 2010-11-09
Thank you!

Maybe I spoke too soon. (NOT about the "Thank you", of course - only in marking Solved!)

Computer Janitor STILL shows the same packages needing cleanup.

---

### Post by Verbeck on 2010-11-09
if you have installed some programs from .deb files (eg. virtualbox) it'll show up there

---

### Post by phubert28 on 2010-11-09
Well, it appears that some of  those in the list appear in the "Removing" messages in terminal... so I'm just wondering why Computer Janitor continues to list them.

One that wasn't removed is "linux-image-2.6.32-25-generic"

**

But, since several install/uninstall related things aren't working following my upgrade, I'm supposing SOMETHING fundamental is broken.

I really do NOT want to have to backup my user space in order to run a FRESH install and of course I'm wondering if the 11.4 upgrade will only break MORE when it comes around.

I am becoming somewhat LESS enamored of Linux vs. Windows as time goes bye (for example, OO really doesn't compete well with MS Office and lots of miscellaneous stuff simply isn't available (like Dymo's Labelwriter software or Rosetta Stone or... (long list)).

---

### Post by phubert28 on 2011-01-20
sudo apt-get autoremove

does NOTHING:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**

I DID find an outstanding bug report for Computer Janitor, listing it as critical, saying it made the program completely non-functional.

Apparently I'm now waiting for the 11.04 -upgrade-
(I really don't want to try a fresh install - backup/restore my files, but if there's a really clear way to do it... like to a USB stick??? Never tried using Linux backup/restore software)

---

### Post by Layvian on 2011-01-20
Haha, Computer Janitor... Oh what a waste.

---

### Post by phubert28 on 2011-01-20
Is there another way to remove old update (including kernel) files????

---

### Post by lbarnes on 2011-01-21
> **phubert28 said:**
> Is there another way to remove old update (including kernel) files????
Synaptic

---

### Post by phubert28 on 2011-01-21
Well, forgive my ignorance, but how does one use Synaptic for that purpose (cleaning up)????

---

