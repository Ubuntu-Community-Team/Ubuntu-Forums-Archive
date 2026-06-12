---
title: "removing dead boot path"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by obsideo on 2009-05-05
i've been using a windows based program (wubi) to install ubuntu. i have recently resized and formatted the vista partion that it was installed on, but due to my impatience i overlooked uninstalling wubi before i did that (yea, a.d.d.). does anyone know how to remove the dead-end boot option on a windows based pc? or could someone please point me in the right direction, whether i need look through windows or ubuntu to clear this out? any help would be very much appreciated.
 thanks,
  sean

---

### Post by cariboo on 2009-05-05
If you have a install CD just boot from the cd and when you get to the where it gives you na option to install or repair, choose R for the recover console. 

Run FIXMBR and FIXBOOT, these to commands will remove grub from the MBR.

---

