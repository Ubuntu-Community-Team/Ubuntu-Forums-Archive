---
title: "Trouble with dual boot."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by djk21108 on 2009-01-12
I have two Os's installed at the moment.  I have Ubuntu and Windows 7.  They're on separate partitions.  I just don't have any idea how to get to Ubuntu.  When I hit the power button on my computer it goes to Windows, how do I choose to go to Linux?

---

### Post by djk21108 on 2009-01-12
Seriously though I think I'm going crazy.  I'm pretty positive I have two OS's.  I just don't know how to access them.

---

### Post by djk21108 on 2009-01-12
Allright I have one of my problems fixed.  Grub is now there. Now how do I get Windows to be on my Grub Menu?

---

### Post by djk21108 on 2009-01-12
I edited my menu.lst thing but that assumed windows was on sda1 mines on sda2.  I'm getting an error 13.  What do I do?

---

### Post by djk21108 on 2009-01-12
I/ve got 

title  Windows 7
root   (hd0,0)
savedefault
makeactive
chainloader  +1

---

### Post by djk21108 on 2009-01-12
Help would be super appreciated.  I can only boot into Ubuntu right now, which might be this forums aim. :)

---

### Post by muteXe on 2009-01-12
Jesus mate, learn some patience :)
Have you checked out the supergrub disk?

Have a read of [http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page) , it might of some help.

---

### Post by Terl on 2009-01-12
And, bear in mind Windows 7 is a beta version so who knows how nice it will be as a dual boot with Linux.  

Did you have windows installed when you installed Ubuntu?

---

### Post by djk21108 on 2009-01-12
woot super grub did the trick.

my last question.

how do i choose which one is my default boot?

---

### Post by mjheagle8 on 2009-01-12
it sounds like you installed windows second, which is always a bad idea bc it trys to take over your computer. you'd have to edit your grub.list to get both oses on it. see this thread for help editing your grub.list. [http://ubuntuforums.org/showthread.php?t=46558](http://ubuntuforums.org/showthread.php?t=46558). 
also, i agree with muteXe, we cant answer instantly. give it a few minutes bro.

---

### Post by drjonze on 2009-01-12
> **djk21108 said:**
> woot super grub did the trick.

my last question.

how do i choose which one is my default boot?

Install 'startup manager'. Its in the add/remove programs or you can type  'sudo apt-get install startup manager ' . You can use this to change the GRUB menu, ie: change/turn off timeout, limit number of kernels displayed and choose the default OS, etc...

---

### Post by mjheagle8 on 2009-01-12
whoops sorry, i didnt see that you already solved that. my bad. yeah, startup manager is an excellent tool if you are going to be changing any settings related to the boot process.

---

