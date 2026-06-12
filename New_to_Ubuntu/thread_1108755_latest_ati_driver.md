---
title: "latest ati driver"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-03-28
i installed the latest ati driver from the ati web site 
it had many improvements with beryl and video 
i later  installed ubuntu updates and now i am confined to vesa
why does it take ubuntu so long to update the debian REPOSITORIES with the latest stuff 
it has taken me months to get a system that works and it seems that everytime i update, it breaks 
first with my network driver
now my graphics  
is there some way of making deb's out of .run and .bin installations 
so that i can add remove stuff

---

### Post by ronocdh on 2009-03-28
If you install something from a source other than the repositories, and another version exists in the repositories, it's a good idea to tell the system not to upgrade (or downgrade). The **aptitude hold** command is useful for this. Use **man aptitude** to read more about it.

Using this, once you get your system in order, you can place a hold on possibly conflicting drivers and keep your system how you like it.

Also, always remember to read carefully what you're downloading and installing, even in a so-called "automatic" update!

---

