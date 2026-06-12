---
title: "Moving home"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by bj218 on 2011-03-05
How do I get around gvfs? see below.

root@bill-desktop:/home/bill# sudo mv /home /home.bak
root@bill-desktop:/home/bill# cp -a /home.bak/* /media/homeu
cp: cannot stat `/home.bak/bill/.gvfs': Permission denied
root@bill-desktop:/home/bill# sudo mv /home.bak /home
root@bill-desktop:/home/bill#

---

### Post by Drate on 2011-03-05
I hate when people start asking questions about "why" you're doing something rather than just answering.  I really do.  So I'll start with:

You shouldn't need to get around it, I doubt it should stop you from doing... whatever it is you're doing there.

But why are you needing to copy the .gvfs?  It is where Ubuntu stores mounts for windows shares and whatnot... typically nothing you need to worry about and most importantly the contents could generally be regarded as temporary.

My recommendation would be to simply cp/mv everything BUT .gvfs and go about your merry!  :)

---

