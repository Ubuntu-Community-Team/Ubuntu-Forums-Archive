---
title: "Can't copy a CD"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by John Peschken on 2010-07-31
Brasero won't copy CD's for me.  It tells me "All required applications and libraries are not installed."

The error message goes on to tell me to manually install:  CDDA2WAV (twice!).  Searching the Ubuntu software center turns up several "Audio Extraction tool for sampling CD's" All but one references "cdparanoia" in one form or another, except one that refers to "yaret".  

I have installed all the cdparanoia stuff assuming I need it all, but same result.  Now what?

---

### Post by gandaran on 2010-07-31
do you have the ubuntu-restricted-extras installed?

---

### Post by mcduck on 2010-07-31
How are you trying to copy the CD?

You shouldn't need those libraries to just make a copy of a disk, as making a simple copy doesn't require the system to actually understand what it's copying..

---

### Post by John Peschken on 2010-08-23
I solved this and other problems by starting with a new install.  Noe I've got a whole new crop of troubles.

---

### Post by rickle on 2011-01-05
I was getting same thing (missing CDDA2WAV twice!)
using Synaptic I Installed icedax (9:1.1.10-1ubuntu1) since it has the cddawave,  and it Fixed it for me.
Ubuntu 10.10 upgraded from 10.04.

---

### Post by manni on 2011-07-19
I had a similar problem with Ubuntu 10.04 using brasero 2.30-2. Disc copy always gave error.
I solved it by first upgrading brasero to 2.31 from ppa by renbag:
sudo add-apt-repository ppa:renbag/ppa.
Then I had to install the icedax package for the missing cdda2wav

---

