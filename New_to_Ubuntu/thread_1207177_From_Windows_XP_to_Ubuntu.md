---
title: "From Windows XP to Ubuntu"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Oceanik on 2009-07-07
Hi all, 
First post here :)

I'm new to Linux and even though I'm quite puzzled by the amount of info in so many places that I'm not sure where to start...

Anyway here is my question:
I plan to buy a new computer and install Ubuntu only on this new box.
Next I want to be able to copy some of my data (.jpg, .doc, .xls, .mp3, .avi, .txt etc) from my WinXP box to my Ubuntu box

1] Is it possible to copy everything and open them in Ubuntu as I would in XP?

2] What is the easiest way to do it? (please , please, keep it simple, I don't know what mounting means for example)

Thanks!

---

### Post by sdlynx on 2009-07-07
1)Yes it is possible to open up those formats on Ubuntu.  Some may require a certain application to open but almost every format is readable on ubuntu.

2If you're moving a lot of stuff I suggest using an external hard drive.  If its not that much just use a flash drive.  Both of those will automount on Ubuntu.

---

### Post by mn_voyageur on 2009-07-07
If you have an older box lying around, you could load ubuntu on it.

MN

---

### Post by Oceanik on 2009-07-07
Thanks!

Re: using an external drive: If I use an external hard drive in NTFS and plug it through the USB port to my Ubuntu computer I can just copy files like that?

The "file manager" in Ubuntu will be able to "convert" the Windows files to the Ubuntu format without me doing anything?

---

### Post by nhasian on 2009-07-07
> **Oceanik said:**
> 1] Is it possible to copy everything and open them in Ubuntu as I would in XP?

Data yes.  Programs no.  If you have music, movies, pictures, word processor or spreadsheet documents you should be able to open them easily with the default programs in ubuntu.

> **Oceanik said:**
> 2] What is the easiest way to do it? (please , please, keep it simple, I don't know what mounting means for example)

get an external hard disk.  good to have for backups as well as moving data.

---

### Post by sdlynx on 2009-07-07
Yeah you see the files aren't 'Windows' files, they're just files.  Ubuntu and Windows can read the same files, the only thing thats different is the way the operating systems journal the files on your hard drive.

---

### Post by Oceanik on 2009-07-07
So from a Ubuntu box you can play (with VLC for example) an MP3 or an AVI that are on a "Windows"  NTFS external hard drive / USB key?

Thanks

---

### Post by Celauran on 2009-07-07
Yes, absolutely. You'll need to install the appropriate codecs to play them, because they aren't installed by default (non-free and all), but their being on an NTFS drive won't pose any problems.

---

### Post by Oceanik on 2009-07-07
Perfect!

Thanks a lot guys!

---

### Post by bigboy_pdb on 2009-07-08
> **Oceanik said:**
> 
1] Is it possible to copy everything and open them in Ubuntu as I would in XP?


You can copy your files, but they won't always open as intended. For example, if you have MS office documents that are complex, that use macros, or where the font, page, and margin dimensions must be an exact size, they may not open in Open Office the way you expect them to. This may occur with other files and programs as well.

Most programs are pretty good, but they're not perfect.

For the most part you can check those programs using a Linux installation, live CD (if it contains a program to open it), or by installing Linux in a virtual machine.

If for the most part you are pleased with the results, you can use a Windows installation in a virtual machine to handle the cases that didn't work out.

> **Oceanik said:**
> 
2] What is the easiest way to do it? (please , please, keep it simple, I don't know what mounting means for example)


You should use an external drive to copy the files (which was mentioned by someone else) or CD/DVD-RWs.

Mounting isn't a complicated concept. If you put a USB drive into your computer with Windows running, it creates a drive letter. If you do it in Linux, it creates a mount point, which is basically a folder through which you can access the files. For example, if you plug in a Kingston USB stick the mount point might be "/media/KINGSTON". From that folder you can access/modify the files on the Kingston USB stick.

---

### Post by Oceanik on 2009-07-08
Good point, I should try to open my most non-regular files.

Unfortunately I don't have enough space to install it on my HD but I can probably run it from a CD.

Thanks

---

