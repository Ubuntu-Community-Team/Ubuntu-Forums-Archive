---
title: "[SOLVED] Why I have 2 kernels"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jay li on 2008-12-12
When Ubuntu starting I see these options:

Ubuntu 8.10. kernel _2.6.27-9_-generic 
Ubuntu 8.10. kernel 2.6.27-9-generic (recovery mode) 
Ubuntu 8.10. kernel _2.6.27-7_-generic 
Ubuntu 8.10. kernel 2.6.27-7-generic (recovery mode) 
Ubuntu 8.10. memtest86+
 
I know it's changed after one of the system updates, so how can I remove the old kernel from the list?

---

### Post by waspbr on 2008-12-12
that is because you have updated the kernel, normally the system sets the boot to the newest kernel. it is often recommended you keep your one previous kernel in case of problems with the new version.

ubuntu won't delete your old kernels for you, you will have to do it yourself,(I forgot exactly what the command is) and remove them from your menu.lst file. 

I wouldn't worry about it.

---

### Post by Kobalt on 2008-12-12
Open the Package Manager and look for the package "linux-image". You'll find kernel 2.6.27-7-generic and be able to remove it if you wish.
However, I should advise you to remove a kernel only after being sure that everything works fine with the new one. Test each new kernel after an update before removing it.

---

### Post by jay li on 2008-12-12
Thank you both, waspbr and Kobalt.

BTW, Kobalt, where is "Package Manager" located?

---

### Post by Michael.Godawski on 2008-12-12
System > Administration > Synaptic Package Manager

---

### Post by s.fox on 2008-12-12
To launch Synaptic, choose **System** > **Administration** > [B]Synaptic Package Manager

EDIT: [/B] Ninja'd :(

---

### Post by meson2439 on 2008-12-12
I don't recommend deleting the old kernel. It might produce problems. It's not too large, so don't worry about the size. The sized saved are just not worth the trouble you might get.

---

### Post by jay li on 2008-12-12
Thanks guys I found it, and I decided to take your advices and keep it that way.

---

### Post by meindian523 on 2008-12-12
and if you wish to keep the old kernel,but just hide it from the boot menu,do
```
gksudo gedit /boot/grub/menu.lst
```and place a Hash(#) in front of the relevant entries ie

> 
title        Ubuntu 8.10
root        (hd0,4)
kernel    /vmlinuz-2.6.27-7-generic root=UUID=f780bda5-460b-453d-81d3-1af3e6de8fb2 ro quiet splash
initrd     /initrd.img-2.6.27-7-generic
to
> 
#title        Ubuntu 8.10
#root        (hd0,4)
#kernel        /vmlinuz-2.6.24-16-generic root=UUID=f780bda5-460b-453d-81d3-1af3e6de8fb2 ro quiet #splash
#initrd        /initrd.img-2.6.24-16-generic


---

### Post by jay li on 2008-12-12
Thanks meindian523.

Can I do the same thing to line:
"_Ubuntu 8.10. kernel 2.6.27-7-generic (recovery mode)_"

---

### Post by meindian523 on 2008-12-12
yeah,to any entry,as many as you wish.That doesn't delete the kernel file or anything,just hides it from the menu.It's called commenting out,FYI.

---

