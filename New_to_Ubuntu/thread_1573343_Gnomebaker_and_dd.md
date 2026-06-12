---
title: "Gnomebaker and dd"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-09-12
Just out of my own curiosity, I was looking at the output of Gnomebaker today while burning an .iso to dvd and I noticed that it seems to be issuing the command:
```
dd if=/home/andrew/Solitary_Man.iso of=/dev/sr1 obs=32k seek=0
```

So, is gnomebaker essentially acting as the GUI interface for dd in this instance?  If so, am I correct to presume that running the same command via terminal will end with the same result?

Also, what do the obs=32k and seek=0 settings mean?

---

### Post by mikewhatever on 2010-09-12
I think the dd command should work, and the obs and seek options are explained in the man file for dd.
from 'man dd':
> obs=BYTES
write BYTES bytes at a time (default: 512)
seek=BLOCKS
skip BLOCKS obs-sized blocks at start of output


---

### Post by saabfordjr on 2010-11-04
I need help ASAP!!!! I can not get GNOMEBAKER to burn a CD. It shows completed but the disk is always blank. WHAT DO I NEED TO DO???

---

