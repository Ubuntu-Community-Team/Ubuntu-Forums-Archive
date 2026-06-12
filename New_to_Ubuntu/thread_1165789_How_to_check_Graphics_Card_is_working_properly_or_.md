---
title: "How to check Graphics Card is working properly or not?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-21
Is there any method to check if my graphics card is working properly or not? May be some Terminal command?

---

### Post by meborc on 2009-05-21
if you wonder about 3d, then i usually just run the "glxgears" command

if you need to know if you have direct rendering try "glxinfo | grep rendering"

to check if graphics card is detected by the pc just run "lspci | grep VGA"

---

### Post by raziiq on 2009-05-21
Thanks for those commands, all are working fine for mean.
Does it mean i have successfully installed my Graphics Card Driver?
Direct Rendering said YES

---

### Post by mcduck on 2009-05-21
> **raziiq said:**
> Thanks for those commands, all are working fine for mean.
Does it mean i have successfully installed my Graphics Card Driver?
Direct Rendering said YES

Yes, if everything seems to be working fine you have full reason to assume everything *is* working fine.. :)

---

### Post by Br1987 on 2011-03-06
Tried all the above test and everything seems fine, but I have a question on this... I can not play internet videos... Everytime I play youtube videos my  computer crashes, I reboot but still the same... something wrong??

---

