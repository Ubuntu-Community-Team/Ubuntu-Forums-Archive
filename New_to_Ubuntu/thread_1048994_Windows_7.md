---
title: "Windows 7"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-01-24
I seem to be having trouble finding an answer via google, and the searches here are timing out. 

could someone tell me if I can dual boot Windows 7 and Ubuntu?  I just built a new PC, installed windows 7, and would like to install Ubuntu now.

Thanks

---

### Post by Zewbie on 2009-01-24
My guess is yes...  just the same way you install a duel boot with any flavor of windows

Install windows first and then make space on your HDD for Ubuntu

---

### Post by Locutus_of_Borg on 2009-01-24
yes you can, i am doing it now


here is grub entry for windows 7
```
title Windows 7
rootnoverify (hd0,3)
chainloader +1
```

you cant install it to an extended/logical partition

you dont need to install windows first as long as you have a linux disk to re-install grub

---

### Post by brandoncolorado on 2009-01-24
> **Locutus_of_Borg said:**
> yes you can, i am doing it now


here is grub entry for windows 7
```
title Windows 7
rootnoverify (hd0,3)
chainloader +1
```

you cant install it to an extended/logical partition

you dont need to install windows first as long as you have a linux disk to re-install grub

If I install Ubuntu after Windows 7, do I have to manually change that grub entry?

---

### Post by leonardo_neo on 2009-01-24
> **brandoncolorado said:**
> I seem to be having trouble finding an answer via google, and the searches here are timing out. 

could someone tell me if I can dual boot Windows 7 and Ubuntu?  I just built a new PC, installed windows 7, and would like to install Ubuntu now.

Thanks

Yes I guess you can.

---

### Post by SunnyRabbiera on 2009-01-24
> **brandoncolorado said:**
> If I install Ubuntu after Windows 7, do I have to manually change that grub entry?

Possibly

---

### Post by Locutus_of_Borg on 2009-01-24
> **brandoncolorado said:**
> If I install Ubuntu after Windows 7, do I have to manually change that grub entry?

the best way to find that out is to do it, then look at the file and see if you need to edit the line or not...

you shouldn't let possibly having to type out ~20 words detract you

---

