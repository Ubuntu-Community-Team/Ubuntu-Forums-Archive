---
title: "upgraded to 9.04 and now bootup keeps asking language/boot device"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by chosenhandle on 2009-07-10
I upgraded to 9.04 from 7.10. 

The upgrade seems successful, except that whenever I reboot the computer, the boot screen stops and asks me a language to use as well as how to boot ubuntu.....from CD, netbook edition and the last option is from first disk. Once I pick first disk, no problem, the system properly boots up and I am good to go.

The reason this is a problem for me is that the computer is run headless and I have to drag a display out of the closet and plug it in and answer those two prompts.

I am pretty sure it is a boot script thing, but I am not experienced enough with linux to know where to look or what to do.

Any assistance is appreciated.

Paul

---

### Post by LewRockwell on 2009-07-10
the BIOS is set to boot from the optical drive first...and you've left the LiveCD in the drive

.

---

### Post by chosenhandle on 2009-07-10
wow...what an amazingly simple answer. Thank you very much. Works like a charm now.

I never even considered something like that when I when I was trying to debug it!

---

