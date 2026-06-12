---
title: "GRUB  move or reinstall?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-02-17
Apparently somehow I got grub installed on disk 4

My system has removeable ide drives and 4 sata drives.

Ubuntu is on a removeable ide. Windows on another removable ide.
That way I plug in one or the other and run.

Ubuntu will boot only if I make the boot priority go to the sata drive. With sata disk 4 is disconnected Linux will not boot. Windows will.

Grub says boots from disk 4. So how do I make linux boot from the ide with no other drive plugged in? I hope you don't say reload!

---

### Post by Titan8990 on 2009-02-17
You should view this guide for installing grub on the correct disc: [http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub)

---

### Post by caljohnsmith on 2009-02-17
I would not recommend following the tuturial that Titan8990 linked to, because that installs Grub to the MBR of whichever is your sda drive. I don't think that is what you want if I'm understanding you correctly. So correct me if I'm wrong, but do you want to install Grub to the MBR of the same drive Ubuntu is on, so then you don't have to worry about if the SATA drive 4 is disconnected in order to boot Ubuntu? If so, how about giving the following a try:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd2,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That's similar to the other tutorial, but the difference is that using "setup (hdX)" instead of "setup (hd0)" ensures Grub is installed to the same drive that Ubuntu is on. Let me know how that goes or if you run into problems.

---

### Post by Al Fischer on 2009-02-17
Tried but how do I get into a 'Terminal' from the CD. Closest option offered is Install'  Looked at alll the options and not a clue. Tried ctrl-alt-F1

Trust me, I am just getting started with Linux!! Much to learn.

---

### Post by Al Fischer on 2009-02-17
Tried about three times when I CAREFULLY re-read the instructions for re-installing grub. It said boot from the DESKTOP CD and I was just grabbing the SERVER CD which doesn't do the trick. Now all is well!

Gotta read more carefully...

---

