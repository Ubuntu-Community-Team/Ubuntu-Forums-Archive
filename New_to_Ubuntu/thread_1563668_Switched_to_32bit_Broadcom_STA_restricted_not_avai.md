---
title: "Switched to 32bit: Broadcom STA restricted not available?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-08-29
Hey all,
   I was using Ubuntu 10.04_64 but recently reinstalled with 32 bit....in the past, because I have a dell with BCM 4312, ive needed to go to System>Admin>Drivers then enable the restricted STA driver to enable wireless.
  Well, when I go to System>Admin>Hardware Drivers, it says lists nothing to Enable.....any thoughts ? 
  
   Thanks!

---

### Post by pastalavista on 2010-08-29
Open System/Administration/Software Sources and make sure restricted and multiverse repositories are enabled (checked). Then, via wired ethernet, run the Update Manager and try the Hardware Drivers tool again.

---

### Post by sandyd on 2010-08-29
> **UbuNoob001 said:**
> Hey all,
   I was using Ubuntu 10.04_64 but recently reinstalled with 32 bit....in the past, because I have a dell with BCM 4312, ive needed to go to System>Admin>Drivers then enable the restricted STA driver to enable wireless.
  Well, when I go to System>Admin>Hardware Drivers, it says lists nothing to Enable.....any thoughts ? 
  
   Thanks!
plugin your ethernet cable and install bcmwl-kernel-source

---

