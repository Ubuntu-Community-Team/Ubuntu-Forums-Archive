---
title: "Cleaning up a very messy GRUB"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by andy1964 on 2010-03-10
**Cleaning up my GRUB.**
 
I've been experimenting with dual boot with 9.10 Karmic and windows 7. 
 
After some adventures (read- mistakes), my initial start-up menu has several copies of 9.10 and the original win7. The partition sizes get smaller with each copy of 9.10. 
 
How can I get rid of all except one 9.10 and win7? I can't do an erase-and-clean-install as, although I have a DVD with 9.10, I do not have the disk for win7 (it came installed on machine). Regretably, I can't lose win7 as need it for work stuff.
 
I've put Start-up Manager on 9.10 to control my default boot-up. I've also set the boot option in win7 to agree with the start-up manager. The systems both work OK - it's just I have a screen full of OS to 'choose' from and small partitions.
 
Help me!
Thanks all, Andy.

---

### Post by Paul T. on 2010-03-10
Not sure if this is what you're looking for but try this link:

[https://wiki.ubuntu.com/Grub2#Removing Entries from Grub2 ](https://wiki.ubuntu.com/Grub2#Removing Entries from Grub2 )

---

### Post by bumanie on 2010-03-10
It would be helpful to see your partition structure could you post the terminal output of > sudo fdisk - lThat is a lower case L, not the digit one. I think you should clone win7 to an external drive so that you can reinstall it in case anything goes wrong. Partitioning tools and installing ubuntu usually works well, but errors can be made.

---

### Post by PPPilot on 2010-03-10
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1423934](http://ubuntuforums.org/showthread.php?t=1423934)

It should lead you through a GRUB clean up....

---

### Post by andy1964 on 2010-03-11
Hi - Lost patience and have just done a clean install of 9.10. Will have to use partner's machine for win apps.
Totally linux now - scary!
 
Thanks for help everyone - I'm sure I could have fixed it if I had more patience than an amoeba!

---

