---
title: "Restore Grub2 after windows 7 install"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by noorez on 2009-12-03
Hey,

I just did a clean install over my windows xp install...and completely forgetting that the windows boot loader overwrites grub...

I remember how to restore the old version of grub but since I'm using the newer one that came with ubuntu 9.10, has the method for restoring grub changed?

Can someone direct me how to restore grub2 ?

---

### Post by coffeecat on 2009-12-03
Have a look at post #1 here: 

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to: [SIZE=2][COLOR=red]How to restore the Ubuntu grub bootloader (9.10 and beyond)

[/COLOR][/SIZE]You need to boot up with the 9.10 live CD, of course.

---

### Post by noorez on 2009-12-11
Hey, 

I gave this a try and it worked.... but the entry in grub still reads windows xp and this menu option will not boot into windows 7. I get an error that the device does not exist(?). I know that the windows installation exists on my hard drive though.

What method do I use to restore grub but have it recheck all the operating systems? The method in the link provided does not re-check operating systems.

---

### Post by mcdjork on 2009-12-11
In Terminal, type:
sudo update-grub2

This will scan your drives and regenerate the boot menu. If Windows 7 doesn't show up, something's wrong.

---

