---
title: "Windows 7, Ubuntu, and Puppy Linux on the same PC?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-24
Hello folks!  I have an exclusive Windows 7 hard drive, and an exclusive Ubuntu hard drive with version Ubuntu 11.04, and the hard drive will choose which operating system to boot into when I select it.  

My question is, can I also install the latest Puppy Linux on the drive that contains Ubuntu 11.04 and it  being in the Grub menu for a choice?  

Do I have to separate the partitions as such or does Puppy Linux give you the choices that Ubuntu makes when installing and fill remaining space when doing a frugal install?

Will all three operating systems be in the Grub menu?

Thanks

---

### Post by wildmanne39 on 2011-05-25
> **TAspr said:**
> Hello folks!  I have an exclusive Windows 7 hard drive, and an exclusive Ubuntu hard drive with version Ubuntu 11.04, and the hard drive will choose which operating system to boot into when I select it.  

My question is, can I also install the latest Puppy Linux on the drive that contains Ubuntu 11.04 and it  being in the Grub menu for a choice?  

Do I have to separate the partitions as such or does Puppy Linux give you the choices that Ubuntu makes when installing and fill remaining space when doing a frugal install?

Will all three operating systems be in the Grub menu?

Thanks
Hi, I know that you can install a third operating system, but I do not know anything about puppy linux.:P

---

### Post by TAspr on 2011-05-25
> **wildmanne39 said:**
> Hi, I know that you can install a third operating system, but I do not know anything about puppy linux.:P

Isn't it just another operating system or do you have to know the ins and out of it first?

---

### Post by wildmanne39 on 2011-05-25
> **TAspr said:**
> Isn't it just another operating system or do you have to know the ins and out of it first?

HI, you asked particularly about puppy linux how the install process is.

---

### Post by migs73 on 2011-05-25
I don't believe Puppy was designed to be installed as a full time operating system, therefore to do so can be a little more difficult.
The instructions to do so are here;

[http://www.puppylinux.com/hard-puppy.htm](http://www.puppylinux.com/hard-puppy.htm)

Good luck

Mike

---

### Post by MoebusNet on 2011-05-25
The advantages of Puppy Linux on Live-CD/USB that have been useful to me are:

1) The image is very small to download (~100 - 140 MB)

2) The included software works as intended; you avoid the risk of breakage caused by updates (often seen in update-releases and rolling-update releases). If an update is required, download the newest complete image.

3) Portability

---

### Post by badrra on 2011-12-06
Quite simple. Two ways actually, since you have a windows and a ubuntu drive. 

1. Ubuntu Drive - Create a folder in root, say puppylinux, and unpack the iso image into that directory. Then if your using grub2 then do an update. ig grub, just update the menulist to include puppy linux and its files. 

2. Windows 7 Drive - you may do the same but you will need grub4dos to update the boot loadeer in windows 7. 

3. Another way is to use unetbootin in either windows 7 or ubuntu. it will also do a frugal install. 

All of the above installation options is what is known as frugal installation of puppy linux. 

For more details, consult google. :P

---

