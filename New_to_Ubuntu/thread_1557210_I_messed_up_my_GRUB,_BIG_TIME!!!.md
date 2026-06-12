---
title: "I messed up my GRUB, BIG TIME!!!"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by gavdari on 2010-08-20
Hi,
First of all, please don't tell me how stupid I am. I know it all.
Now the problem:
I wanted to get rid of the BURG (the fancy grub) after removing the  related packages from synaptic, so with root access, I deleted all of the Burg folders I  found, in /boot and home directory and another place which I can't remember. now, Grub  doesn't load at the start up. It gives and error which reads: "File not  found, Entering rescue mode". and then the console changes to something  like "grub rescue>". Please tell me how can I rebuild grub without  losing my data on Ubuntu?

---

### Post by SoFl W on 2010-08-20
Did you try "sudo update-grub2"?  I am not sure it would help, but it is a start.

---

### Post by gavdari on 2010-08-20
sudo is an unknown command for grub rescue. when I boot with ubuntu live cd, it says that grub is not installed and I should Install it by sudo apt-get install grub.

---

### Post by maikel.b on 2010-08-20
Hello, everyone has once  in a lifetime problems with LINUX..

Maybe you can put your install cd or dvd in the computer and boot from the rescue menu and try to reinstall the grub and maybe the kernel for a boot? 

With the cd or dvd you can rescue the installed server/desktop what is it of an installation>?

Is it a server or a desktop? with the desktop cd you can use the F1 key and the F4 key...

Greetz

---

### Post by Shpongle on 2010-08-20
you can reinstall grub with the live cd to your primary partition. this should help its for duel booting but it will tell you how to restore grub [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by gavdari on 2010-08-20
I guess the tutorial that Shpongle posted worked. but now when I boot it goes straight to grub console. how can I return back the menu?

---

### Post by Shpongle on 2010-08-20
did you type sudo update-grub , after you restored grub ? , this should restore the menu

---

### Post by gavdari on 2010-08-20
this is what I get when I run sudo updat-grub:
[HTML]/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)[/HTML]

---

### Post by Shpongle on 2010-08-20
see here , another user had the same error and fixed it [http://ubuntuforums.org/showthread.php?t=1434354](http://ubuntuforums.org/showthread.php?t=1434354)

---

### Post by gavdari on 2010-08-21
well at last this one fixed it:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) - METHOD 3 - CHROOT

---

