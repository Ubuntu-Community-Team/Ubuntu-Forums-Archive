---
title: "Help me!!!"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by 10Digits on 2010-01-26
Hi there, 

I was helping a friend installing Scientific Linux v5.4 on his Dell 1420 laptop, the installation was not working at first but today morning my friend was able to install the linux on his computer..but now it seems we cannot boot into the windows vista partition..The grub menu shows us the option to boot into windows but it restarts everytime it is being loaded.

We are totally helpless!!!I have no idea about Red hat linux I can only understand ubuntu [only a little bit!]...please help us out..

 thanks in advance...:P

---

### Post by Wataru8675 on 2010-01-26
Are there two options to boot into?  I know my Vista has two, and one works and one doesn't (not sure exactly what the second is).

---

### Post by J V on 2010-01-26
I'm assuming thats a derivative of ubuntu? (By the way, lots more people would help if you had a more descriptive title)

install startupmanager if it is, and run update-grub to reset the bootmenu, then it should work...

---

### Post by Miljet on 2010-01-26
Vista throws a fit if some other program modifies its partition. For future information, always use the disk tools in Vista to shrink the Vista partition first, then install the Linux Operating System in the free space.

For what you have now, I think you will have to use the Vista recovery disk to repair the Vista boot and then let Vista run a disk check to satisfy itself that all is well. That may overwrite the MBR. If it does you will have to reinstall GRUB.

---

