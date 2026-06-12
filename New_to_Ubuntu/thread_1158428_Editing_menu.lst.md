---
title: "Editing menu.lst"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Fzang on 2009-05-13
Can I simply change the title of the entries in menu.lst to change my grub screen? It seems easy enough but I want complete confirmation because I don't want to mess up something

And also, on a side note, is it possible to use a custom resolution for grub images? I'm trying to use StartUp-Manager (is there a better alternative) and it has various resolutions but not mine

---

### Post by NHArticleTen on 2009-05-13
yes, you can change them to whatever names you would like.

If you have difficulty with editor privileges got to terminal and sudo gedit into whatever you want to edit.

---

### Post by Prospero2006 on 2009-05-13
Backup the original menu.lst and make sure you have a live cd handy in case you mess it up. You can always replace the backup and be ok.

---

### Post by MrWES on 2009-05-13
> **Fzang said:**
> Can I simply change the title of the entries in menu.lst to change my grub screen? It seems easy enough but I want complete confirmation because I don't want to mess up something

And also, on a side note, is it possible to use a custom resolution for grub images? I'm trying to use StartUp-Manager (is there a better alternative) and it has various resolutions but not mine

Yes you can, but I believe your changes will be over-written upon the next kernel update; I believe menu.lst is rewritten automagically.

Bill

---

### Post by 73ckn797 on 2009-05-13
Change only the title (first) line to whatever!

You can also down load "nautilus-gksu" from Synaptic and would be able to open with administrator privileges from within the file browser instead of opening terminal and entering command line stuff. You would right click over the document, such as "menu.lst" and "open as administrator". Useful if you do not want to use terminal. It will not eliminate the need for terminal but is helpful when editing certain system files. It will pronpt for a password.

---

### Post by MrWES on 2009-05-13
> **73ckn797 said:**
> Change only the title (first) line to whatever!

You can also down load "nautilus-gksu" from Synaptic and would be able to open with administrator privileges from within the file browser instead of opening terminal and entering command line stuff. You would right click over the document, such as "menu.lst" and "open as administrator". Useful if you do not want to use terminal. It will not eliminate the need for terminal but is helpful when editing certain system files. It will pronpt for a password.

Wouldn't Alt + F2 and then
```
gksu gedit /boot/grub/menu.lst
```
do the same thing? Shrug...

---

### Post by sir_nasty on 2009-05-13
Side note, last time I checked there was no way to over-ride grub's default screen resolutions.

---

### Post by 73ckn797 on 2009-05-13
> **MrWES said:**
> Wouldn't Alt + F2 and then
```
gksu gedit /boot/grub/menu.lst
```do the same thing? Shrug...


YEP.

Anything wrong about offering alternatives?

---

### Post by MrWES on 2009-05-13
> **73ckn797 said:**
> YEP.

Anything wrong about offering alternatives?

Certainly not -- it's the core of linux, no? I actually haven't heard of that Nautilus plugin, so I learned something new. It seems I had to restart X for the plugin to take effect.

Thanks,
Bill

---

### Post by 73ckn797 on 2009-05-13
> **MrWES said:**
> Certainly not -- it's the core of linux, no? I actually haven't heard of that Nautilus plugin, so I learned something new. It seems I had to restart X for the plugin to take effect.

Thanks,
Bill

Yes it works great. Really nice when searching for a file to open as administrator so easily.

I also had to logout and in for it to take effect.

---

### Post by mcduck on 2009-05-14
> **MrWES said:**
> Yes you can, but I believe your changes will be over-written upon the next kernel update; I believe menu.lst is rewritten automagically.

Bill

Only a part of the file is rewritten during kernel updates, namely the section marked as "debian automagic kernels list". The rest of the file doesn't change, and the defaults section inside the automagic kernels list will stay through the updates as well.

The important thing is if you need to change any kernel boot options/settings, make sure you do the same change in the default settings section as well. Otherwise defaults will overwrite your changes on next kernel update.

(and if you add any entries of your own, or move them around, keep them outside of the automagic kernels list..)

---

