---
title: "Issues from Ubuntu 9.04 64-bit on on i386 machine"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-20
ok so here are my problems:
skype for linux 64-bit doesn't work for me
AIM won't install
When I try to shutdown, the screen goes black after signing me off, but the power button stays lit meaning it's still on >_<
help plz...me = noob
also, is there any way to transfer data from xp? (I dual boot)

---

### Post by Game Over on 2009-05-20
Hey there! I'm a n00b to Linux as well but here is my advice...

I would try using Pidgin instead of AIM, it comes bundled with Ubuntu and it accomplishes the same goal only better.

Ekiga = Skype for Linux on your architecture.

If you need to install Widows wares, you'll need Wine, which is found under Add/Remove.

Hope this works.
~Alva

As for transfering data, I just backed up my files on a CD-R and plunged straight into Ubuntu (after I got everything working, of course). It up to you, but if it's and option, I would highly recommend it.

---

### Post by anewguy on 2009-05-20
A couple of questions/suggestions:

Do you see briefly at boot a message saying BIOS to old ACPI not supported or some such thing?  If so, you need to edit your menu.lst file and add the acpi option - you can search this forum to find info on it and what to specify.

Is your Windows XP on the same physical disk as Ubuntu?  If so, it should already be mounted and you should be able to copy files from it.

If your Windows XP is on a different disk but still in the same computer, you may just need to mount it.

Dave :)

---

### Post by rlj399 on 2009-05-20
oh thanks a lot guys
about the messages during boot, i'll check time i start my computer, but I don't think so.
How do I know if my xp files are already mounted?

---

### Post by anewguy on 2009-05-21
For me, my Windows drive (back when I still had Windows) just showed in the places as xxxxgb disk (whatever the size was).  Also, I believe the entry for the menu.lst would be to add acpi=force on the kernel line.

If you don't know, menu.lst is located in the /boot/grub and must be edited as super user or root (use a terminal window then sudo gedit it).

Here's a copy of a section from my menu.lst file:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet:)


What you would want to do is in the similar entry for you go to the kernel line and add a space and acpi=force to the end of the line.

You have to reboot before it will take effect.

Dave

---

### Post by donkyhotay on 2009-05-21
How are you installing skype? I use the 64bit versions of ubuntu and don't have any problems with installing/using skype. Course I cheat and use the [medibuntu repositories](http://www.medibuntu.org/) which makes installation of skype a cinch regardless of architecture. In regards to AIM, I would recommend doing what someone else suggested and just use pidgin instead.

---

### Post by lisati on 2009-05-21
Huh? I don't get it.....
>  Issues from Ubuntu 9.04 64-bit on on i386 machine

I didn't realise the 80386 was a 64-bit CPU..... or am I missing something here?

---

### Post by rlj399 on 2009-05-21
ohhh, i found my xp files :-) and i downloaded medibuntu and was able to install the 64 bit skype ^_^
thanks a lot guys, i can breathe easy now:D
However...i was wondering if with this medibuntu program i could get itunes and transfer my music?

---

