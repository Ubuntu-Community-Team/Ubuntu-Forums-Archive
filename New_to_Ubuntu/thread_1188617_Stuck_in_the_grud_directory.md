---
title: "Stuck in the grud directory"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Windy Peaks on 2009-06-15
Hello All in the Forum:

This one happen out of the blue, nothing changed or repaired or even tried out of the normal stuff.

I have Ubuntu 8.10 on My hard drive with nothing else ( no dual anything) Anyway When I turn on the computer the boot up stops very quickly and I find myself in a terminal window with "GRUB" at the beginning of the line.
no ubuntu@ubuntu or root@ubuntu nothing normal.

I used a live disk to check out the "device.map" and that looks normal but thats where I'm stuck.
I cannot get the computer to finish booting up.

Any thoughts Folks ???

Thanks for any help in advance.

Windy

---

### Post by Sealbhach on 2009-06-15
Try this when you get to the grub command line:

[B]find /boot/grub/stage1

[/B]
      [B]setup (hd0)

[/B]
type **quit** and **reboot**.

.

---

### Post by Windy Peaks on 2009-06-16
Thaks for Your input but no luck following Your directions.

When I first switch the computer on the top of the screen reads.

[ Minimal BASH-like line editinng is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

grub>


when I tried your instuctions everything looked good at first the second command returned found boot/grub/stage1 and boot/grub/stage2 then at the end I get 

Running "install /boot/grub/e2fs_stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage1/boot/grub/menu.1st"...succeeded
Done.
grub>



I type quit and it returns error 27: Unrecongnized command
so for laughs I type reboot which works fine but when the computer comes back to life we are at the same grub directory ???

I hope this detail is useful in determining the problem.

Thanks again 
Windy

oh one other thing is that sometimes your first command makes my floppy drive vibrate and then returns (hd0,0).
There is nothing in the floppy drive, never has been. ???

---

### Post by Sealbhach on 2009-06-16
Ok, thanks for the very clear feedback. It's strange that Grub does not recognise the "quit" command
and this would suggest to me that your Grub installation has become corrupted in some way. It would probably be best to reinstall Grub, which you can do from a Live CD.

There's some clear instructions on how to do that here:

_[http://fosswire.com/post/2009/5/restoring-overwritten-grub/](http://fosswire.com/post/2009/5/restoring-overwritten-grub/)_

You'll need to be very careful though, or you could wreck your system. If you're feeling brave, go for it, otherwise wait for some other answers. Good luck. :)

.

---

### Post by iponeverything on 2009-06-16
Boot the live CD.

open a terminal and run:


```

sudo bash
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt /dev/sda

```

---

### Post by Windy Peaks on 2009-06-17
Thanks for Your input, but still no change right back to where I began. 

Could there be some phsyically wrong with the hard drive it's self ????
What Do You Forum types think ???

Windy

---

### Post by Windy Peaks on 2009-06-24
Ok this may not be the only answer but it was the one I settled on.

I gave up trying to repair the grub file and loaded Ubuntu 9.04 using the entire hard drive.
After going through the entire loading procedure I got to the point where You reboot and remove the live disk. Upon powering up I got the grub file error 17, I was certain that the hard drive was boogered (not working like it should)
I thought that as a last result I would try XP on it just get away from the grub issues, then I remembered that Fedora 10 has a LILO or GRUB option so I tried that instead. 
Windows are good for looking through and not much more, so I'll stick to Fedora 10 on My desktop and Ubuntu 9.04 on My laptop.
I am currently reading "Beginning the Linux Command Line" So I need both systems anyway. 

Windy

---

