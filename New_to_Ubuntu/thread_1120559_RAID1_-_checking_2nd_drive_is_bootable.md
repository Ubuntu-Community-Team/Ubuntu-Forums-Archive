---
title: "RAID1 - checking 2nd drive is bootable"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by sentofuno on 2009-04-09
hi all, i was following a guide on installing 8.10 on RAID1 - which works fine, i've been using it for weeks - but can't find the link i was following regarding the 2nd part of making the 2nd drive bootable with grub.

now i'm unsure if i follow a different guide to the letter it will work on my setup. i'm not as knowledgeable as i'd like to be to experiment and go messing up a perfectly good install. could anyone help me check? for refeence the guide i was using is similar to, but ISN'T, [http://kuparinen.org/martti/comp/ubuntu/en/raid.html](http://kuparinen.org/martti/comp/ubuntu/en/raid.html)

thanks

---

### Post by Didius Falco on 2009-04-09
There is no way, of course, to know what guide you were originally following, but I've found this site to be very trustworthy:

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

I couldn't find anything specific to 8.10, but I also couldn't find any indication that it had changed.

You could compare this one to the one you are looking at now and see if they match.

Hope it helps...

---

### Post by miegiel on 2009-04-09
You probably need to edit /boot/grub/menu.lst

If you open it in an editor you'll find blocks like :
```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=38e8bdc4-7656-49d4-b415-2ec3cbe99e60 ro quiet vga=791
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

I think it's enough to copy and paste your default boot option and edit it a little.

[LIST]
[*]Edit the **title** line so you know it's the 2nd disk in the menu.
[*]Change the **root** line to "root (hd1,0)"
[*]Maybe you also need to change the **UUID**, I'm not sure about that.
[/LIST]

Blocks with # in front of the lines are just examples. The 1st block without lines starting with # is the 1st option/line you see in your boot menu.

---

### Post by sentofuno on 2009-04-09
ok i have edited that file like this:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro  
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic !!DISK 1!!
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro  
initrd		/boot/initrd.img-2.6.27-11-generic
```

so it now reads 

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro  
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic !!DISK 1!!
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro  
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/md0 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/md0 ro  
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/md0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

is this correct? i am assuming every kernel update will automatically add the second drive as well? my system does not appear to have UUID specified so i can ignore this right?

thanks both very much for the help.

---

### Post by miegiel on 2009-04-09
Looks good to me, did you try if it works yet?

Keep an eye on what happened with the grub menu after the next kernel update. I think you'll need to edit the menu.lst again, but who knows, grub might be more intelligent than I expect.

---

### Post by Didius Falco on 2009-04-09
> **sentofuno said:**
> is this correct? i am assuming every kernel update will automatically add the second drive as well? my system does not appear to have UUID specified so i can ignore this right?

thanks both very much for the help.

I don't _think_ the kernel updates will add the second drive, but once you get the menu.lst set up initially, it's easy enough to add it. You'll know the first time the boot menu comes up.

Personally, I use the UUID  system. It's attached to each drive and never changes unless you reformat the drive, but if you've cloned the the first drive to the second one, they may have the same UUID.

If you run ```
 ls -l /dev/disk/by-uuid/
```  from a terminal window, it will list your drives by UUID.

It may work better for you to not use the UUID and simply add to the title, like you've already done.

---

### Post by sentofuno on 2009-04-09
i've used the boot prompt to make sure both options boot ok, and they do. thanks very much for the help! i'll remember to check after the next kernel update for any changes.

much appreciated

---

### Post by Didius Falco on 2009-04-09
No problem - besides, I learned some things about setting up and running Raid 1.

---

### Post by sentofuno on 2009-04-24
i installed jaunty last night, in case anyone was wondering it detected a custom menu.lst during the update.

i took the option of allowing it to revert it back to normal, and editing manually afterwards per instructions above.


cheers again for the help

---

