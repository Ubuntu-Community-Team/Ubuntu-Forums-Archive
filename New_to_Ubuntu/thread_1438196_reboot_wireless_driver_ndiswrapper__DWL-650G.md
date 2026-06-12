---
title: "reboot wireless driver ndiswrapper  DWL-650G"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by funguspsylocibe on 2010-03-24
hello everybody!
I know that about this card there are so many posts but I didn't find yet a solution to get an automatic turn-on of my card (DWL-G650+) when I boot (or reboot) my laptop.
This is my last terminal:

matteo@matteo-laptop:~$ sudo depmod -a
[sudo] password for matteo: 
matteo@matteo-laptop:~$ sudo modprob ndiswrapper
sudo: modprob: command not found
matteo@matteo-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
matteo@matteo-laptop:~$ 

I am new about xubuntu and I need and help please](*,)

HELP ME PLEASE!

Thanks a lot!

---

### Post by jimv on 2010-03-30
Try this command:

```
sudo ndiswrapper -m
```

Then reboot and see if it starts the card automatically.

---

### Post by anewguy on 2010-03-30
And the other way is to add ndiswrapper to the extra modules you want loaded for the kernel at boot.  the ndiswrapper -m is supposed to essentially do this, but sometimes doesn't seem to take. This will do it.  To do so:


cd /etc

sudo gedit modules

go to the end of the file and add this line:

ndiswrapper

save the file, exit and reboot.


Dave ;)

---

