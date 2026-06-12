---
title: "How to see files on hard drive when booted to live CD"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-09
I am running Jaunty from the live CD.  I need to see the files on my hard drive which has a non working installation of Jaunty already installed on it.

If I open a terminal window (Applications>Accessories>terminal) I can type

ls -l

and see all the files that the live CD operating system is using.  What commands do I need to use (in terminal) to do the same thing for the files on the hard drive?

Thanks in advance.

---

### Post by jenkinbr on 2009-06-09
Instead of doing this from the terminal, I would open nautilus, click the computer button on the toolbar, and then open whichever drive is the one you want.  Not sure which drive that is?  Try them all. (I'm sometimes doubtful as to which one is which, as they are listed by drive capacity, exept in the rare case that the drive has a label.

---

### Post by Hobgoblin on 2009-06-09
Or just go to places and select the drive, it will then be auto mounted for you.

---

### Post by raymondvillain on 2009-06-09
Wonderful advice, but Nautilus is NOT WORKING as of this writing (1:55 P. M.)  I don't know why, either.  This is an HP desktop (about 4 years old) with a Pentium 4 and 3 gigabytes of RAM.

If I click on "places>Desktop" a tab opens up at the bottom of the screen that says "opening Desktop", then it goes away after a while.  Nautilus never opens.

I get a message box saying
"Sorry, the program "nautilus" closed unexpectedly
Your computer does not have enough free memory to automatically analyze the problem and send a report to the developers."

Any ideas?

---

### Post by prshah on 2009-06-09
> **raymondvillain said:**
>  I need to see the files on my hard drive which has a non working installation of Jaunty already installed on it.


You should use recovery mode (from grub) rather than the live CD.

However, this method will work for either mode.

Open a terminal (Applications-Accessories-Terminal) (In recovery mode, you will be dumped to the terminal).

Give the command ```
sudo mkdir /media/sdXX && sudo mount /dev/sdXX /media/sdXX -o defaults,rw
```

Replace sdXX with the partition ID of the partition you want to open; use the command ```
sudo fdisk -l
``` to find the partition id.

This will create a directory in /media/ with the name of your partition id, which in turn will contain all your files.

Post back with details if you have any difficulties.

---

