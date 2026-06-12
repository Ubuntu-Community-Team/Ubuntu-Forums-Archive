---
title: "Graphics driver"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by CsG_kieran_2 on 2011-04-05
Hey, I need help with a graphics driver from ATI/AMD. (Its for the X1250 integrated - Ub 10.10)
I have followed the instructions from the AMD website but when it asks me to open it through the terminal with; 

"sh ./ati-driver-installer-9.2-x86.x86_64.run". 

I get "sh: Can't open ./ati-driver-installer-9.2-x86.x86_64.run"
?

I Don't think i have installed any drivers from Nvidia or VIA (Am not that stupid :KS). Maybe the openGL drivers, but I can't say...

Any help?

---

### Post by jocko on 2011-04-05
That is an OLD driver (9.2=February 2009). Neither the kernel nor the x server in 10.10 is supported by that driver, so there is no point in trying. And ati/amd have not and will not release any newer driver that supports your card.
Stay with the open source driver. It's the only one that works.
(and the error message you get suggests that either the file is not executable or that you're not working in  the correct directory. But don't try to install it. It will break your graphics completely.)

---

### Post by CsG_kieran_2 on 2011-04-05
](*,)

Saved me a bunch there m8. 
Problem is, the open drivers can't cope with 1080p playback, something that was a breeze on W7. 

Can I improve performance somehow?

tnx.

---

### Post by Mark Phelps on 2011-04-05
> **CsG_kieran_2 said:**
> ]Can I improve performance somehow?

tnx.

Probably not enough to make a difference.  

You really need the restricted drivers -- and as already mentioned, ATI dropped support for those for your card years ago.

---

### Post by CsG_kieran_2 on 2011-04-05
It wont be a problem anyway.

Thanks for the help you two, appreciated :)

---

