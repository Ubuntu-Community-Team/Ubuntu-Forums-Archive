---
title: "Shutdown Error"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by fslezak on 2009-05-30
Hello. 

I can't shut down Ubuntu properly ever since I changed hard disks.

I used to have Windows on the hard disk that came with my computer. The Shutdown worked fine. I think that the system is having a BIOS eror as my computer is very old. It is about 12 years old.

What happens is that Ubuntu shuts down but my computer stays on. All it does is show the "System Halted" signal. I need to turn it off with the power switch.

Any suggestions to shut it down completely?

---

### Post by doctorbighands on 2009-05-30
It sounds like you're dealing with an ACPI issue on a machine of that age. AFAIK, the BIOS on older machines didn't support ACPI until about 2000 or so. In this case, you're doing everything you can do to shut the machine down - Ubuntu is taking it as far as it can, and you have to actually physically cut the power. There's no way that I know of to have software cut the power for you on an older machine.

---

### Post by Didius Falco on 2009-05-30
You could check and see if there are any Bios updates for your PC, but with a 12 year old PC, I wouldn't count on it.

Regards,

Didius

---

### Post by anewguy on 2009-05-30
You can also just add acpi=force to the kernel line in the menu.lst for grub.  That normally takes care of it.  menu.lst is located in the /boot/grub folder, and you must be super user or root to edit it.  Since you already have a running system, try the following:

(1) open a terminal window (applications/accessories/terminal)

(2) log on using your normal user id and password

(3) type the following:

cd /boot/grub<press enter> This changes the default folder you are working in to /boot/grub - where the menu.lst file exists.

sudo cp menu.lst menu.lst_good<press enter>  This saves a copy of the existing file in case you mess up.  If it asks for a password just use your normal password.

sudo gedit menu.lst<press enter>  This opens up the GUI editor and loads in the menu.lst file.

(4) Scroll down until you see a section similar to this:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

That should be at the end of the file.  Now, position the cursor back to the end of the 1st line that says "kernel"  - in my example above it would be the line that reads:

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro quiet splash 

After the word "splash", press the space bar and add the following:

acpi=force

Now, save the file, exit the editor, type "exit" to exit the terminal window, then restart.  After this restart, try doing a shutdown - your system should power off now.

Dave :)

---

### Post by rochep on 2009-05-31
Thanks for the clear steps anewguy, it fixed the issue for me.

---

### Post by anewguy on 2009-05-31
You're welcome!

Dave :)

---

### Post by fslezak on 2009-06-01
I will show your post to my other programmer. Hopefully it will fix my error. Just something else, I have Ubuntu 8.04. WILL THIS WORK???

---

### Post by anewguy on 2009-06-04
The addition of noapic, acpi=force, etc., you can do in 8.04 with no problem.

Dave :)

---

### Post by fslezak on 2009-06-21
Actually, when I do this, the system starts "probing" sound. I can't figure out how to fix this.

Any suggestions?

---

