---
title: "Live CD 10.04 Customization Boot Error /boot/casper/initrd.gz"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-07-06
Anyone know why I get this on my live cd customization, the normal live cd works fine, when I go to customize it, I get this with a OK button below it and then it does nothing.

This is at the start up screen, anyone got idea's? suggestions?
Thanks in advance!

---

### Post by drs305 on 2010-07-06
I don't know exactly what steps you have taken or from the site you are using, but the initrd file in the *casper* folder of the Ubuntu LiveCD iso in the past few releases of Ubuntu has been initrd.**lz** rather than initrd.**gz**.

That could very well be your problem.

---

### Post by ericeclifford on 2010-07-06
> **drs305 said:**
> I don't know exactly what steps you have taken or from the site you are using, but the initrd file in the *casper* folder of the Ubuntu LiveCD iso in the past few releases of Ubuntu has been initrd.**lz** rather than initrd.**gz**.

That could very well be your problem.

very true, I did however make sure that the initrd file was indeed gz, maybe there is a script pointing to it?

I used an old script I made for 8.04.2 customizations, maybe I am telling the wrong commands or something.

Actually You just made me think of something :),

thanks, ill let you know if it works!

---

