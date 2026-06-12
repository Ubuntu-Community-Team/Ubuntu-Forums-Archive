---
title: "ATI and Fujistu N6460"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by worthog on 2009-05-15
I've got a Fujistu N6460 laptop with a HD 2600 card and running Ubuntu 8.04.  I have installed the ATI driver and things seem to work ok until I tried google earth.   GE opens up but the map screen flashes contantly.  Other 3d apps don't work particularly well either.  
I am not sure how to tell what version of ATI driver I have installed, but I do know it is on.(I have run fglrxinfo)
Is there a setting I need to change in xorg.conf?  Do I need a different version of ATI driver?
Thanks in advance!

---

### Post by lavinog on 2009-06-16
I think the later versions of the proprietary driver (starting with 9-4) fix this problem.

The problem you are experiencing is due to desktop effects. Turning off desktop effects should stop the flickering.

---

