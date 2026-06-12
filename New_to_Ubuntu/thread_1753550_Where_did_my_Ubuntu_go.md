---
title: "Where did my Ubuntu go???"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by cake nom nom on 2011-05-09
Hi i just dual booted Ubuntu 11.04 on top of windows 7

and windows 7 just boots up automatically

help?

anyone know where can look or what I can do to make it so it's a choice which OS I want to boot up? 

I have windows 7 64 bit
Ubuntu 11.04 32 bit

Could that be why?

thanks in advance!

---

### Post by diablo75 on 2011-05-09
How exactly did you install it?

---

### Post by Grenage on 2011-05-09
Ahoy there;

Did you install Windows 7 after Ubuntu?  Windows would replace Grub with its own boot manager, so you'll need to reinstall grub.  There is some pretty comprehensive information [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), on the Ubuntu help site.

---

### Post by cake nom nom on 2011-05-09
Nope I installed window 7 first then Ubuntu
as I said I dual booted Ubuntu on top of windows 7

I followed a guide 

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
and this one for steps that weren't so clear on the one above

[http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html](http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html)


I first installed windows 7 

then made a new partition using the disk management in windows

then i split that partition because I was following a guide on how to share files between the two O'S 

I hadn't gotten to that step yet

I just installed Ubuntu on one of the halves of the newly split partition

---

### Post by Grenage on 2011-05-09
For some reason Grub has probably not been installed to the boot sector of the drive you're booting from.  Installing Grub in the way shown in my initial link should get that done, and give you a grub menu at boot time.

---

