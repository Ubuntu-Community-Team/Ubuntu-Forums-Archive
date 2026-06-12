---
title: "Adding other Ubuntu repositories"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-02-11
Hey, everyone! I installed Ubuntu on my second laptop, and then I installed the LXDE. There are some problems with the file manager in Karmic, but I hear that the pcmanfm package (I believe this is the file manager) works well for Lucid.

So, some questions:

1. Can I use packages from other releases of Ubuntu?
2. How do I add the repository for other releases? Do I just go into sources.list, and copy and paste all the URIs while replacing "karmic" with "lucid"?

I know I can just install the package, but I think I can learn something if I try this method first. :p

---

### Post by Temposs on 2010-02-11
Changing your existing repositories from karmic to lucid would more or less upgrade your system to lucid(but the structure would still be that of karmic, since you didn't run an distribution upgrade or install as lucid), assuming you installed all of its recommended updates. In other words, something would probably break if you did that.

You could change the repositories to lucid, upgrade pcmanfm, and then change all the repositories back to karmic. That's probably your best bet, using the kind of method you're thinking of.

---

### Post by mathfreak123 on 2010-02-11
Thank you for the quick reply! I changed all my repositories to lucid, upgraded pcmanfm, and then changed them all back to karmic. This has solved my problem in LXDE.

(If anyone's curious, the problem was that the file manager couldn't do file associations.)

---

