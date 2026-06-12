---
title: "Problems with ubuntu 8.10"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by rtowsley on 2009-03-24
Hello, I have a PC with two hard drives- one Windows and the other Ubuntu. I tried downloading and installing ubuntu 8.10 and it locks up at the sign on page. Only option is to reboot. when I am using windows it does not recognize my hard drive with ubuntu. I would like to reformat the ubuntu drive and go back to ubuntu 8.04 which was good. at booting my cumputer I have to (using grub) choose between ubuntu and windows. (only windows works). What do I need to do to correct this problem? Rich

---

### Post by KCG102282 on 2009-03-24
If all yo are doing is reninstalling HArdy just insert the disk and install over the Intrepid partition

---

### Post by rtowsley on 2009-03-24
I have done that and it still ends the same way. The screen locks up on the screen name page and can only reboot. I have both downloaded 8.10 and disc mailed to me by ubuntu both with same problem.

---

### Post by SikEnCide on 2009-03-24
Boot with the 8.04 Hardy disc and try using Gparted to wipe the Ubunut partion. Then try and reinstall Ubuntu.

---

### Post by rtowsley on 2009-03-24
What is gparted? Where do I find it?

---

### Post by sandyd on 2009-03-24
meaning
go boot up livecd

go to ACcessories => Terminal
tyoe in 
```

gparted
```
theres your nice ubuntu partition manager

partitions with the filesystem called "ext3" are ubuntu
partitions with the filesystem called "swap" is ubuntu
you have to delte both.
remember to swapoff the swap partition (right click -> swapoff) first.

---

### Post by rtowsley on 2009-03-24
Hello again, I got onto ubuntu using livecd. When I typed in gparted it said I did not have access to the root so the command could not be completed. It also said that I could use the command sudo -u username to be able to access it as a non-root user. This didn't work because I don't have a username that the version knows.What next? Rich

---

### Post by t0ddy on 2009-03-24
whith live-cd just write sudo before de command that it works

hey, the linux partition is ext2 or ext3, windows does not recognize it, fortutately there is v-fat that works with both

sometimes the ubuntu so have some troubles with video card, just google-it to solve the problem

sorry about en-us, I do speak pt-br

---

### Post by sandyd on 2009-03-28
> **rtowsley said:**
> Hello again, I got onto ubuntu using livecd. When I typed in gparted it said I did not have access to the root so the command could not be completed. It also said that I could use the command sudo -u username to be able to access it as a non-root user. This didn't work because I don't have a username that the version knows.What next? Rich
ooooooohhhhhhhhhhhhhhh

me making a big mistake here](*,)

type ```
 sudo gparted
```not ```
 gparted 
```

---

