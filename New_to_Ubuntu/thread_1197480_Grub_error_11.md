---
title: "Grub error 11"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Xscapist on 2009-06-26
Im using ubuntu jaunty 64bit 9.04 for starters.

I installed SUM (startup manager) and try to change my grub background when i restarted i got the picture but when i attempt to launch jaunty it comes up with an error (error 11: unrecognized device string). Im on vista atm dual booting. this is the um boot that jaunty tries to do i guess.

root 371a4be-aac1-4735-93b4-0a4d0c929c8a

kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=371a4abe-aac1-4735->

initrd /boot/initrdimg-2.6.28-13-generic

quiet

savedefault

i believe my jaunty boots on (hd0,4) if that helps......vistas boot says.

rootnoverity (hd0,0)

savedefault

makeactive

chain loader +1 


I dont really know what info helps in this situation im new to ubuntu..:confused:

---

### Post by SteveDee on 2009-06-26
> **Xscapist said:**
> Im using ubuntu jaunty 64bit 9.04 for starters.

I installed SUM (startup manager) and try to change my grub background when i restarted i got the picture but when i attempt to launch jaunty it comes up with an error (error 11: unrecognized device string). Im on vista atm dual booting. this is the um boot that jaunty tries to do i guess.

root 371a4be-aac1-4735-93b4-0a4d0c929c8a

kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=371a4abe-aac1-4735->

initrd /boot/initrdimg-2.6.28-13-generic

quiet

savedefault

i believe my jaunty boots on (hd0,4) if that helps......vistas boot says.

rootnoverity (hd0,0)

savedefault

makeactive

chain loader +1 


I dont really know what info helps in this situation im new to ubuntu..:confused:

I don't know if you manually typed this info or did a copy/paste from menu.lst, but there are some errors.

initrd /boot/initrdimg-2.6.28-13-generic should be initrd /boot/initrd.img-2.6.28-13-generic

The kernel line should have the full UUID and boot options, something like this:-
/boot/vmlinuz-2.6.28-13-generic root=UUID=371a4be-aac1-4735-93b4-0a4d0c929c8a ro quiet splash vga=771

There are variations in menu.lst which seem to be due to the grub version in use, but the root line looks wrong to me. This would normally be something like; root (hd0,0)

There may also be a UUID line like this:-
uuid 371a4be-aac1-4735-93b4-0a4d0c929c8a

Your device.map file should contain references to all hard drives.

---

### Post by billgoldberg on 2009-06-26
> **Xscapist said:**
> Im using ubuntu jaunty 64bit 9.04 for starters.

I installed SUM (startup manager) and try to change my grub background when i restarted i got the picture but when i attempt to launch jaunty it comes up with an error (error 11: unrecognized device string). Im on vista atm dual booting. this is the um boot that jaunty tries to do i guess.

root 371a4be-aac1-4735-93b4-0a4d0c929c8a

kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=371a4abe-aac1-4735->

initrd /boot/initrdimg-2.6.28-13-generic

quiet

savedefault

i believe my jaunty boots on (hd0,4) if that helps......vistas boot says.

rootnoverity (hd0,0)

savedefault

makeactive

chain loader +1 


I dont really know what info helps in this situation im new to ubuntu..:confused:

Something seems wrong with that, as the poster above me said.

Did Startup Manager comes from the repositories or did you download it somewhere from the internet?

Because that seems like a serious bug. 

Not hard to fix, but still.

---

### Post by Xscapist on 2009-06-26
yeah i typed it out guess i did make mistakes dont know how to plainly copy it, and SUM had a package from the internet.

root 371a4be-aac1-4735-93b4-0a4d0c929c8a
/boot/vmlinuz-2.6.28-13-generic root=UUID=371a4be-aac1-4735-93b4-0a4d0c929c8a ro splash vga=773
initrd /boot/initrd.img-2.6.28-13-generic
quiet
savedefault

think thats how it looks exactly..
i dont really know how to do much.. so details are helpful lol.

---

### Post by SteveDee on 2009-06-27
> **Xscapist said:**
> yeah i typed it out guess i did make mistakes dont know how to plainly copy it, and SUM had a package from the internet.

root 371a4be-aac1-4735-93b4-0a4d0c929c8a
/boot/vmlinuz-2.6.28-13-generic root=UUID=371a4be-aac1-4735-93b4-0a4d0c929c8a ro splash vga=773
initrd /boot/initrd.img-2.6.28-13-generic
quiet
savedefault

think thats how it looks exactly..
i dont really know how to do much.. so details are helpful lol.

I recommend you download SuperGrub and use this to try to fix your Grub configuration. You basically create a CD of SuperGrub, boot your system with it, and then try some of the menu options to fix Grub.

SuperGrub link: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by louieb on 2009-06-27
When you get to the grub menu highlight the Ubuntu entry. and press e to edit.

change 
```
[COLOR=Red]root[/COLOR] 371a4be-aac1-4735-93b4-0a4d0c929c8a
```to
```
[COLOR=Red]uuid[/COLOR] 371a4be-aac1-4735-93b4-0a4d0c929c8a
```root is used when you grubs partition naming. example
```
root (hd0,4)
```Note this change is temporary. If it works will have to modify /boot/grub/menu.lst for it to stick.

---

