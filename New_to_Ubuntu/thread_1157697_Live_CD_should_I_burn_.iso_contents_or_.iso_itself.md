---
title: "Live CD: should I burn .iso contents or .iso itself? (And will a DVD work?)"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by VgnStirfry on 2009-05-13
I was about to burn a new Live CD when I received this option:[INDENT]**Create disc containing a single disc image file?**
It appears that the disc, when created, will contain a single disc image file. Do you want to create a disc from the contents of the image or with the image file inside?
[/INDENT]Which is the right choice?

Also, I plan to burn onto a DVD (I am out of CDs and have to complete this now). Will the Live CD environment work properly if burned onto a DVD? 

Thanks!

---

### Post by lisati on 2009-05-13
Burn it as a "disk image". Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

EDIT: Putting it on a DVD should be fine: I've resorted to that trick on one or two occasions and haven't run into problems (yet)

---

### Post by logos34 on 2009-05-13
> **VgnStirfry said:**
> 
Will the Live CD environment work properly if burned onto a DVD? 


works for me.  Although I can't recall if I've gone beyond using the live desktop session and actually installed successfully

---

### Post by ravi_buz on 2009-05-13
If u use nero use the option burn image to disk and not make a cd option

---

### Post by VgnStirfry on 2009-05-13
> **lisati said:**
> Burn it as a "disk image". Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Thank you, I've seen that, but the directions do not address what to do when the person encounters the dialog I copied and pasted, above.  

[s]I think you have told me to burn the entire image file, rather than the contents of the file, onto the disk.  Is that correct?[/s] 
Reading the instructions, I discovered that I am not sure what I am supposed to do. **lisati**, you said to burn it as an image, but the instructions you linked say: *"[Step] 7. After burning completed, verify that your CD contains multiple files and folders and not just the ISO file. This way you will know the process was performed correctly." * These instructions seem contradictory to me.

Can anyone help clear this up?

---

### Post by Didius Falco on 2009-05-13
> **VgnStirfry said:**
> Thank you, I've seen that, but the directions do not address what to do when the person encounters the dialog I copied and pasted, above.  

[s]I think you have told me to burn the entire image file, rather than the contents of the file, onto the disk.  Is that correct?[/s] 
Reading the instructions, I discovered that I am not sure what I am supposed to do. **lisati**, you said to burn it as an image, but the instructions you linked say: *"[Step] 7. After burning completed, verify that your CD contains multiple files and folders and not just the ISO file. This way you will know the process was performed correctly." * These instructions seem contradictory to me.

Can anyone help clear this up?

Hi,

When you burn it as an image, it extracts the files from the ISO file to the CD/DVD and recreates the contents of the ISO file on the CD/DVD.

If you burn it as a file, you will wind up with a CD/DVD that contains a file named filename.ISO, which, for the purposes of a working bootable Live CD is worthless.

Did you see my last post in the 800x600 thread, and get a gui working again?

Regards,

Didius

---

