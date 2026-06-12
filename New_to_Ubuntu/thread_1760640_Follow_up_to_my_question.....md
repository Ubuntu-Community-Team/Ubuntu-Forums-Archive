---
title: "Follow up to my question...."
date: 2011-05-17
forum: New to Ubuntu
---

### Post by abhishes on 2011-05-17
I posted this question here [http://ubuntuforums.org/showthread.php?t=1760447](http://ubuntuforums.org/showthread.php?t=1760447)

Which I was able to resolve by the advice given.

However I am noticing that each time I boot my VM I have to repeat these steps.

Can you tell me a way in which I can automatically boot without entering these lines?

Thanks for your help.

---

### Post by falko on 2011-05-17
Boot into your virtual machine, then run
```
grub
```
and enter the lines. That should do the trick.

---

### Post by Lateralis on 2011-05-17
My guess is that Grub was broken during the upgrade.  When you are inside your VM install, try typing 

```

sudo update-grub

```

from the command line.  That should remake /boot/grub.cfg and point the entries to the correct locations.

---

### Post by abhishes on 2011-05-17
I entered this command


administrator@ubuntu:~$ sudo update-grub
[sudo] password for administrator: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
administrator@ubuntu:~$ 


I booted my machine... but I had to enter the same stuff on the grub> console.

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinux root=/dev/sda1 ro
initrd /initrd.img
boot

when the machine booted successfully. I again did


administrator@ubuntu:~$ sudo update-grub
[sudo] password for administrator: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
administrator@ubuntu:~$ 

But still when I rebooted, it tool me to the grub> console and I had to enter all the steps to boot.

So sudo update-grub is not solving the problem of automatically booting the ubuntu desktop.

---

### Post by YesWeCan on 2011-05-17
Try 'sudo grub-install /dev/sda'

Grub is in 3 sections and the second of these may have become alienated from the third. Grub-install reinstalls the first two sections. When you put in those manual boot commands you are telling the second part where to find the third part.

---

### Post by abhishes on 2011-05-18
yes!

sudo grub-install /dev/sda

---

