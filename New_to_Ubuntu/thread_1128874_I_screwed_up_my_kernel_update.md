---
title: "I screwed up my kernel update"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by eddski on 2009-04-18
I did an update and I did not allow the update to change my menu.lst file( I did not know what it would do, now I know). Now I cannot boot with the new kernel update, as it is not in my menu.list file. How do I go about adding it to thee menuj.lst?

---

### Post by roger_1960 on 2009-04-18
Hi

I did exactly that a while ago.

You can manually edit menu.1st

First open it with gedit - its in the /boot/grub/ folder, and have a look at it.

There are two groups of lines for each kernel version.  You need to creat two new sets of lines with the kernel version changed to that of the "missing" new kernel.  Leave all the existing lines in the file.

Before you do this, make a backup of menu.1st (thats a figure one) - often there is already one there called menu.1st~ 

In order to do the edit you will need to use > gksudo gedit from terminal to give you root permissions and enter your password.  Do be careful when editing!  When its done, reboot and it should use the latest kernel in the file.

If you are not sure about this, ask more questions _before_ you do it!

---

### Post by Malta paul on 2009-04-18
You did the safest thing buy not changing your boot menu. Just follow the clear instructions given by roger_1960.
I usual only edit the 'Recovery mode' at first, and then reboot with this mode and if all goes well, edit the 'normal' boot mode. If it won't boot you still have the normal boot with the old kernel. Bye the way you can remove old kernels using Ubuntu Tweak 0.4.7
Have fun ;)

---

### Post by eddski on 2009-04-18
how do I find out the new kernel name?

---

### Post by nandemonai on 2009-04-18
Wont a sudo apt-get update-grub detect all installed kernels and rewrite the list for you? Or is that only a grub-install...

---

### Post by Malta paul on 2009-04-19
You can check which Kernel you are using by going to:
system>administration>system monitor>system
;)

---

### Post by roger_1960 on 2009-04-19
Hi again

Yes, thanks nandemonai, that should work - I didn't know the command existed!  This would be eddski's best method.

---

### Post by eddski on 2009-04-20
thanks for the suggestions, though, I figured it out by practicing editing a copy of my menu.lst file and using Malta paul's tip...I'm rockin (even though the sharks lost)

---

