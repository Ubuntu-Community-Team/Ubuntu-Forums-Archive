---
title: "migrated wubi without installing GRUB - what can i do"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by pstjohn on 2011-06-07
Hi all,

I was having some problems with my dual boot setup. I used wubi to install ubuntu inside windows 7, and then decided to migrate it to its own partition using the migrate shell script. However, I elected not to install the grub bootloader (I realize now this was a mistake, however on my previous computer I was unable to boot to any operating system after removing the linux partition - was trying to avoid that eventuality)

Everything was working fine - it used the windows bootloader first, then went to GRUB after selecting ubuntu, where I had the choice between the wubi install or the stand-alone partition. However, once I removed the wubi install, I lost the ability to boot to ubuntu. I tried both easyBCD and an Ubuntu boot cd (which might have been bad, could be my fault), neither of which helped me boot to the ubuntu partition.

I re-installed a wubi partition just to gain access to the stand-alone install, which works, but definitely isnt the solution I'm looking for. My question is - how can I remove the wubi partition without uninstalling the grub loader? Whats the best way to handle this situation?
Again, I'd prefer not to have grub be my primary bootloader, since I've had bad experiences messing with the windows boot sequence. (although if its the only/easiest way, I suppose I'll manage :P)

Thanks!!
Peter

---

### Post by bcbc on 2011-06-07
Use easyBCD. It works on Vista/7. I personally haven't used it, but it seems to be very commonly used.

OR just remember this:
When you want to uninstall Ubuntu... 
_Step1_
Insert your Windows 7 Repair CD (which you can create from Windows) and boot to a repair prompt, then run:
```
bootrec /fixmbr
```

_Step2_
Make sure when you boot, that you boot straight to Windows or the Windows boot manager.

_Step3_
Remove the Ubuntu partition.

If you do step 3 first then you have to stare at a grub rescue prompt until you do step 1.

---

