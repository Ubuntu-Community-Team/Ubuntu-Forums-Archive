---
title: "Can't install from disk, i do not get the option to install"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by DFord425 on 2010-10-25
I just downloaded 10.10 and was burned it to a CD-RW(not sure if that matters) and tried to install it on my laptop. When i booted to the CD, it booted to a command prompt and i had no option to install. Could i have burned it wrong? I can see the files on the disk and i can even search the directory structure (including the CD) using the command line like if it was installed on the hard drive. Has anyone else seen this?

---

### Post by migs73 on 2010-10-25
Is it possible you downloaded the 'alternate' .ISO. This is a text based installer for PC's with low end graphics?
Or the server version? It doesn't have GUI either?

---

### Post by DFord425 on 2010-10-25
I guess its possible, I thought i selected the desktop version from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) but i could be wrong. 

But even if i selected the alternate or server, wouldn't i still be given an option to install? When i booted to the CD, i was not given and option to install.

---

### Post by migs73 on 2010-10-25
> **DFord425 said:**
> I guess its possible, I thought i selected the desktop version from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) but i could be wrong. 

But even if i selected the alternate or server, wouldn't i still be given an option to install? When i booted to the CD, i was not given and option to install.

I've no idea!!! It was the only way I could think of you getting the CLI from a disc but no GUI.Have you tried typing;```
startx
```at the CLI? This should (if it exists) start the X environment (GUI).

If nothing I would download the ISO again and do a md5 checksum on the file before and after burning to disc. Then try again.

EDIT; It is definitely a command prompt? i.e. ubuntu@ubuntu:~$
If it is just a flashing cursor on a black screen, search the forums as this is a common problem (can't remember the resolution though!!)

---

### Post by DFord425 on 2010-10-25
It has a different message than ubuntu@ubuntu:~$ but its acts like a command prompt. I can give the exact message when i go home for lunch in about an hour and a half. Also, it does the Ubuntu loading graphic like its trying to load the GUI then it goes to the "command prompt." i will be able to give exact message, but it says something about not being able to mount something. Sorry i left that part out before.

---

### Post by migs73 on 2010-10-25
> **DFord425 said:**
> It has a different message than ubuntu@ubuntu:~$ but its acts like a command prompt. I can give the exact message when i go home for lunch in about an hour and a half. Also, it does the Ubuntu loading graphic like its trying to load the GUI then it goes to the "command prompt." i will be able to give exact message, but it says something about not being able to mount something. Sorry i left that part out before.

As your avatar suggest;'Good things come to those who wait.':P

I could fair go a pint of the black stuff right now.

---

### Post by DFord425 on 2010-10-25
I boot into BusyBox v1.15.3 and i also get this message:
> (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/Output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by DFord425 on 2010-10-25
Also, instead of getting this prompt ubuntu@ubuntu:~$, i get this prompt (initramfs)

---

### Post by psusi on 2010-10-25
Looks like the disk you burned is no good; try another.

---

### Post by DFord425 on 2010-10-25
Ok, i will give that a try later, thanks.

---

### Post by DFord425 on 2010-10-26
I got a CD-R and re-burned the image and it worked. Thanks for the help.

---

