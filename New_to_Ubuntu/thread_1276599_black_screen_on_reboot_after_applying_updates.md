---
title: "black screen on reboot after applying updates"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by dreamer565 on 2009-09-27
I recently applied the patches that the system manager suggested to my ubuntu 9.04 PC.  It then required a reboot, and after the reboot, I get a black screen after it loads instead of my normal desktop.
 
I have already tried selecting an older kernel from the boot list, the top line is -
kernel 2.6.28-15-generic (which i have been using for a while), I tried using the kernel 2.6.28-14-generic, no luck there either, same black screen.
 
I next tried using recovery mode, and various options - first tried to repair broken packages (since it broke after applying patches) and that didn't help, next tried the file system check - all is good, also tried xfix to auto repair graphic problems, and even tried the fsck file system check.  After each option I would try the "resume normal boot" each time, I got the same black screen after everything loaded.
 
i can boot to a root shell prompt but have no clue as to what to do while there.
 
I looked up the problem to see if i could find a solution, but all the threads I could find describe trying to boot from an older kernel (which was what I tried first), or to try some of the other steps i'd already tried.  I have even tried going back to kernel 2.6.28-11-generic with no luck.
 
any help on what I can do to get my desktop back would be greatly appreciated!!!

---

### Post by grturner on 2009-09-27
do you run nvidia? i was reading elsewhere on the forums that nvidia users were having problems such as that after the update.

---

### Post by dreamer565 on 2009-09-27
Also found these instructions somewhere:
 
>  
Follow these steps to correct the problem.
1. Select recovery mode from the boot menu.
2. Select login as root from the menu in recovery mode.
3. Type this at the prompt
# sudo apt-get remove xorg-driver-fglrx
# sudo dpkg-reconfigure -phigh xserver-xorg
4. Exit
# exit
5. Now select Resume normal boot from the menu.


But no luck there either.  when i did the sudo apt-get remove xorg-driver-fglrx, i got that no such file exists.  Still got the black screen after login.

---

### Post by dreamer565 on 2009-09-27
yes, and i did have problems with my drivers once before.  but that time i was able to roll back to another kernel.  but perhaps i'll follow that rabbit down the hole and look for nvidia driver issues.
 
Thanks!  I'll let ya know.

---

### Post by dreamer565 on 2009-09-27
my bad.  I don't have nvidia drivers on this pc.  It is a Dell with the intel video drivers.  i did have some problems before, but not like this.

---

