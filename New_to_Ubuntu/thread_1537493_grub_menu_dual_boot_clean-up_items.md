---
title: "grub menu dual boot clean-up items"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by henry cow on 2010-07-23
I have an XP / Lucid dual boot system, and the boot menu keeps growing.

I now have 3 kernels, with 2 variations each, 2 memory tests, and Windows XP.

Clean and lean is how I like everything, on general principles. What do I really need from this list?

I think I know how to manage it with Startup Manager.

thanks,

---

### Post by matrixblue on 2010-07-23
I would leave all the kernels there in the unfortunate event that something goes wrong. But if you must then remove the oldest kernel entry and it's recovery mode from /boot/grub/grub.cfg
[B][U]
Be careful with editing this file[/U][/B]

---

### Post by philinux on 2010-07-23
> **henry cow said:**
> I have an XP / Lucid dual boot system, and the boot menu keeps growing.

I now have 3 kernels, with 2 variations each, 2 memory tests, and Windows XP.

Clean and lean is how I like everything, on general principles. What do I really need from this list?

I think I know how to manage it with Startup Manager.

thanks,

Use synaptic package manager. Use say quick search and type linux. Mark for removal the older kernels. I generally leave 2 installed.

---

### Post by linux18 on 2010-07-23
don't forget to ```
 sudo update-grub  
``` after you remove the kernels to clean up the grub.cfg and boot menu.

---

### Post by philinux on 2010-07-23
> **linux18 said:**
> don't forget to ```
 sudo update-grub  
``` after you remove the kernels to clean up the grub.cfg and boot menu.

Removing kernels via synaptic runs update-grub automagically.

[http://www.google.com/m/search?client=ms-palm-webOS&channel=bm&q=ubuntu%20forum%20remove%20old%20kernels](http://www.google.com/m/search?client=ms-palm-webOS&channel=bm&q=ubuntu%20forum%20remove%20old%20kernels)

---

