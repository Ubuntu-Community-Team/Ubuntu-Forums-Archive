---
title: "Bootin with grub"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by lolol i r linux noob on 2009-04-10
Hi am new with linux and i was just wondering how to boot ubuntu from a grub command line. Just in case. A no how to do windows but cant find any help with linux tht works.

Im using ubuntu 8.10
Linux kernel=2.6.27-11

Thanks.

---

### Post by Dileeshvar on 2009-04-10
Hope I answered your question :D !!

[http://ubuntuforums.org/showthread.php?t=1029968](http://ubuntuforums.org/showthread.php?t=1029968)

:guitar:

---

### Post by lolol i r linux noob on 2009-04-10
Cant see how this helps me.

But thanks for answering quickly.

---

### Post by Dileeshvar on 2009-04-10
If still you have anything in mind post it
clearly we will solve it ;)

---

### Post by Hospadar on 2009-04-10
Why do you need to boot ubuntu from a grub command line?

Probably your best bet is when you see the grub menu, hit (whatever key it says) to go into command mode, then I think e to edit the boot lines.  This will give you a good idea of what the boot line is supposed to look like, and if you need to add extra boot options you can do it there.

If you need to make aformentioned changes permanent, you'll have to edit your /boot/grub/menu.lst file.

---

### Post by meierfra. on 2009-04-10
```
root (hd0,4)
kernel /vmlinuz root=/dev/sda5  ro
initrd  /initrd.img
boot
```


This assumes Ubuntu is on /dev/sda5. If not "(hd0,4)" and "/dev/sda5"  need to be adjusted.

You can determine  what number to use for (hd0,4) by typing

```
find /boot/grub/stage2
```

---

### Post by egalvan on 2009-04-10
> **Hospadar said:**
> Why do you **need **to boot ubuntu from a grub command line?


His first message stated... **just in case**

So he seems to have no **need** , just curiosity.. :)

Probably wants to learn more of the Linux thing!

---

### Post by lolol i r linux noob on 2009-04-10
ive tried what meierfra suggested but it doesnt work properly

---

### Post by meierfra. on 2009-04-10
What exactly happened? Any error messages? Are you sure you used the correct values for (hd?,?) and /dev/sd??

Also I forgot to mention that  you need to type "boot" at the end.

---

### Post by lolol i r linux noob on 2009-04-10
A assumed i would have to type boot. And when i did load of text came scrolling onto the screen and it failed. kernel panic or something. A cant remember.

I have no specific reason as why i need to boot from command line a just want to be prepared in the case of a grub failure or somethin.

---

### Post by meierfra. on 2009-04-10
> kernel panic or something.

Sound like you got the "/dev/sd??" part wrong. (Look at the output of "sudo fdisk -lu" in a Ubuntu terminal, to figure out the correct parameters)

Or you could use 

kernel /vmlinuz root=UUID=uuid_of_your_ubuntu_partition  ro

(Type "uuid" in the grub command line to determine the correct UUID's)

---

### Post by lolol i r linux noob on 2009-04-11
it is dev/sda5

and after the vmlinuz do i type 2.6.27-11-generic or not.

---

### Post by meierfra. on 2009-04-11
> vmlinuz do i type 2.6.27-11-generic or not.
/vmlinuz is a link to /boot/vmlinuz-2.6.27-11-generic. So /vmlinuz  should work.  (And  the error message you got is from the kernel, so grub was able to reach the kernel)

Could you post the exact error messages you  are getting?
Are you using some special "kernel parameters" to boot Ubuntu? (Have a look at your menu.lst with  "gksudo gedit  "/boot/grub/menu.lst")
You might try to use the exact same kernel line as in "menu.lst"

---

### Post by lolol i r linux noob on 2009-04-11
i got it working but thanks any way

---

### Post by meierfra. on 2009-04-11
> i got it working 
How?

---

### Post by lolol i r linux noob on 2009-04-11
a forgot to put inintrd once a did it worked.

---

### Post by meierfra. on 2009-04-11
> a forgot to put inintrd once a did it worked. 

O.K.

>  just want to be prepared in the case of a grub failure or somethin.
To be even more prepared, get [SuperGrub ]("http://www.supergrubdisk.org/")

---

### Post by lolol i r linux noob on 2009-04-11
what is super grub

---

### Post by meierfra. on 2009-04-11
SuperGrub is   a CD (or USB or floppy) which lets you reinstall Grub, restore the Windows MBR, and boot into Linux or Windows. If SuperGrub is not able to fix your booting problem automatically, you can also use it to obtain information for further trouble shooting. 

Checkout out the link I provided in my previous post for the details.

---

### Post by lolol i r linux noob on 2009-04-11
if i had heard about this early i would would not have had to trash my computer and start again. 

I had deleted my ubuntu partition along with grub so i couldnt load any os any more.

---

