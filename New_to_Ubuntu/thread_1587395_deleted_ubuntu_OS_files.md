---
title: "deleted ubuntu OS files"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-10-03
Oops, I deleted everything on my Ubuntu partition. Here the long story how it happened. if you want short, go to paragraph 3.

I attempted to install Ubuntu on my flash drive via live DVD a couple of weeks ago. It is an 8GB flash drive, and i have partitioned it so that it has a 6 GB ext4 partition, and a 2GB NTFS partition. all good. I then attempted to install Ubuntu on it. I left the install running an went some where to do something. (i dont remember what, it is unimportant.) I was running the computer on a borrowed graphics card, (I havent bought a new one yet. [http://ubuntuforums.org/showthread.php?t=1562424]("http://ubuntuforums.org/showthread.php?t=1562424")) It is my brother's graphics card. So, I set the install up and left it running, when i came back, the card was not in the computer, so i assumed my brother had it. He did, and when I asked him how the install went, he said that it didn't work and it had come up with an error. he had no idea what the error was of course. so he said just turned off the computer, and took the graphics card out. later, (yesterday to be exact) I got permission to borrow that graphics card again. I went in, and since i had no idea how the install went, I deleted everything that i thought was on the ext4 partition on my flash drive. I was actually deleting everything on my Ubuntu partition that i was was running my computer from. (almost no errors!) when i had finished completely demolishing my Ubuntu partition and Ubuntu itself, i finally realized that it was not my flash drive that i was removing the files from, it was my hard drive. oops. 0_o

I deleted everything on my Ubuntu partition when i thought i was clearing out my 8GB flash drive. (very few errors!)

I have no idea where all the files went, because I deleted all of the ones i could see. Does Ubuntu put them in a hidden folder, and keep them so they can be restored? If so, how would i restore the files, and keep their original structure, from a Fedora partition (if it boots, I might have deleted that to) or from a ubuntu live DVD?

The partition had some file that i would rather not lose, since i worked really hard on them.

---

### Post by Rubi1200 on 2010-10-03
For data recovery options see here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

To be honest, though, I would not get my hopes up too high. Mark it down as a learning experience to be never repeated!

Good luck!

---

### Post by sandyd on 2010-10-03
> **DaGeek247 said:**
> Oops, I deleted everything on my Ubuntu partition. Here the long story how it happened. if you want short, go to paragraph 3.

I attempted to install Ubuntu on my flash drive via live DVD a couple of weeks ago. It is an 8GB flash drive, and i have partitioned it so that it has a 6 GB ext4 partition, and a 2GB NTFS partition. all good. I then attempted to install Ubuntu on it. I left the install running an went some where to do something. (i dont remember what, it is unimportant.) I was running the computer on a borrowed graphics card, (I havent bought a new one yet. [http://ubuntuforums.org/showthread.php?t=1562424](http://ubuntuforums.org/showthread.php?t=1562424)) It is my brother's graphics card. So, I set the install up and left it running, when i came back, the card was not in the computer, so i assumed my brother had it. He did, and when I asked him how the install went, he said that it didn't work and it had come up with an error. he had no idea what the error was of course. so he said just turned off the computer, and took the graphics card out. later, (yesterday to be exact) I got permission to borrow that graphics card again. I went in, and since i had no idea how the install went, I deleted everything that i thought was on the ext4 partition on my flash drive. I was actually deleting everything on my Ubuntu partition that i was was running my computer from. (almost no errors!) when i had finished completely demolishing my Ubuntu partition and Ubuntu itself, i finally realized that it was not my flash drive that i was removing the files from, it was my hard drive. oops. 0_o

I deleted everything on my Ubuntu partition when i thought i was clearing out my 8GB flash drive. (very few errors!)

I have no idea where all the files went, because I deleted all of the ones i could see. Does Ubuntu put them in a hidden folder, and keep them so they can be restored? If so, how would i restore the files, and keep their original structure, from a Fedora partition (if it boots, I might have deleted that to) or from a ubuntu live DVD?

The partition had some file that i would rather not lose, since i worked really hard on them.
You can try using photorec _. [https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

---

### Post by DaGeek247 on 2010-10-04
im not looking to restore the individual files, i would rather not have to install the OS again. (I will if i have to) It took me a while to get the programs i wanted on there, and it will take time again. I believe that Ubuntu puts all deleted file in .trash file right? couldn't i just restore all those files?

thank you for your help.

---

### Post by sandyd on 2010-10-04
> **DaGeek247 said:**
> im not looking to restore the individual files, i would rather not have to install the OS again. (I will if i have to) It took me a while to get the programs i wanted on there, and it will take time again. I believe that Ubuntu puts all deleted file in .trash file right? couldn't i just restore all those files?

thank you for your help.
 /home/<username>/.local/share/*Trash*/files

If you used the rm command, they wont be there.

---

### Post by DaGeek247 on 2010-10-04
I did not use the rm command, i deleted the files via the graphical interface. So i could simply run DSL or Ubuntu via live DVD, and simply copy all those files to the main ubuntu partition, and it would work again?

---

### Post by kidknapp on 2010-10-04
> **DaGeek247 said:**
> I did not use the rm command, i deleted the files via the graphical interface. So i could simply run DSL or Ubuntu via live DVD, and simply copy all those files to the main ubuntu partition, and it would work again?
This is the first time I have heard this proposed. Its worth a shot if all of your data is in that trash folder, but if you deleted it as su and botched the install that badly I would first see if you can even still access the folder from any live OS. If so you may have solved your own problem. If nothing else write back with your results- I'm very curious as to how this will play out.

---

### Post by DaGeek247 on 2010-10-04
all right, i will tell you how it goes, although its not reasurring knowing that this hasn't really happened before... :P

---

### Post by DaGeek247 on 2010-10-12
I have attempted three different live disks to duplicate or backup the files in the .trash-0 folder. yes it is there, but no, i can't access it. in the Ubuntu 10.04 and Fedora 13 disks, it said the access was denyed, and im not even allowed to copy the files. in the DSL live disk, i couldn't find my partition that had Ubuntu on it.

What is a small (50MB to 100MB)  bootable linux system that can restore files that were deleted via graphical interface, but not from the trash?

---

### Post by DaGeek247 on 2010-10-14
bump...

---

### Post by SlugSlug on 2010-10-14
> **DaGeek247 said:**
> I have attempted three different live disks to duplicate or backup the files in the .trash-0 folder. yes it is there, but no, i can't access it. in the Ubuntu 10.04 and Fedora 13 disks, it said the access was denyed, and im not even allowed to copy the files. in the DSL live disk, i couldn't find my partition that had Ubuntu on it.

What is a small (50MB to 100MB)  bootable linux system that can restore files that were deleted via graphical interface, but not from the trash?

from ubuntu live disk termianal run ```
gksudo nautilus
```

---

### Post by DaGeek247 on 2010-10-14
What does the code do? I know that sudo is part of the code to install stuff, but the computer i deleted it on, i have no access to the internets with.

---

### Post by SlugSlug on 2010-10-14
it will open ubuntus file browser with root rights -- so you can open that trash folder and move files

---

### Post by DaGeek247 on 2010-10-16
it worked, but it didnt have the files i needed, so i just removed everything. Since 10.10 came out, im just gonna install it there. thanks for the help guys!

---

