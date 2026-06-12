---
title: "moving files"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by gurt on 2009-06-28
I have some files on a USB drive that I want to transfer to a dir that is owned by root.

I plug in the USB. I see the files in File Browser. I open another File Browser to the dir I want to copy the files into and try to drag them. Fails due to file permission.

How do I do this with the gui? Is there a way to sudo drag files?

I also tried using the terminal. I looked at where the files are located by looking at properties. Says /media/JING'S USB. So I use a terminal and go to /media/JING's USB. Hmmm.

bam@mingus:~$ cd /media/JING'S USB
> dir
> ls -l
> pwd
> exit
> quit
> help
> me
> 

where am I? where are the files? how do I get out of here?

---

### Post by zeroseven0183 on 2009-06-28
Open the File Manager/browser as root. But it's not recommended because you might mess things up. It was designed to be that way.

---

### Post by ~sHyLoCk~ on 2009-06-28
You need an escape "\" after JING's since it will read the "blank space" between JING's and USB. You are doing everything correct. Just use this:

```
cd /media/JING'S\ USB
```

---

### Post by lloyd_b on 2009-06-28
> **~sHyLoCk~ said:**
> You need an escape "\" after JING's since it will read the "blank space" between JING's and USB. You are doing everything correct. Just use this:

```
cd /media/JING'S\ USB
```

Or just wrap the directory name in quotation marks```
cd "/media/JING'S USB"
```which also deals with the issue of that single quote, which is what was actually causing the ">" prompts...

Lloyd B.

---

### Post by egalvan on 2009-06-28
> **gurt said:**
> 

How do I do this **with the gui**? Is there a way to sudo drag files?

bam@mingus:~$ cd /media/**JING'S USB**


To do this with the GUI, open a terminal and type

```
gksudo nautilus
```

this opens nautilus in "root" mode...


there is also a nautilus extension that allows opening folders and files in administrative mode, 
but I don't recall the exact name...

I* think* it is

nautilus-actions

hopefully someone can recall it...


And as an aside,,, I suggest not using folder/file names with spaces in them....
this can get confusing under Linux...
yes, as others have stated, there are work-arounds using "escape" keys,
but I find it easier to avoid spaces... (besides, it's more "Linux")

Use underline or dash instead of space...

JING'S[COLOR="Red"]_[/COLOR]USB

JING'S[COLOR="Red"]-[/COLOR]USB

---

### Post by Miljet on 2009-06-28
I hope that you know what you are doing copying files to a directory owned by root. But, it is your system, so here goes. Open a terminal and type in:
```
gksu nautilus
```
After entering your password, it will open a file browser with root permissions so be careful. You only need one session of nautilus open to copy files. Navigate to the USB stick that contains the files. Select the files to copy, right click on one of them, and select "copy" from the menu. Now navigate to the directory you want to copy the files into, right click, and select "paste" from the menu. All done!

Be sure to close the nautilus window immediately when done.

---

### Post by ~sHyLoCk~ on 2009-06-28
> **lloyd_b said:**
> Or just wrap the directory name in quotation marks```
cd "/media/JING'S USB"
```which also deals with the issue of that single quote, which is what was actually causing the ">" prompts...

Lloyd B.

Damn, I thought I had put that :P Thnaks for pointing out.

---

### Post by gurt on 2009-06-28
Solved! I went with gksu nautilus.

Thanks for all the fast responses!

---

### Post by egalvan on 2009-06-28
> **Miljet said:**
> I hope that you know what you are doing copying files to a directory owned by root. 

Be sure to close the nautilus window immediately when done.

Just because it is "owned" by root doesn't mean it doesn't "belong" to the user.

I bought a 750GB :p, set it up with an external USB device, formatted it to ext3, tried to move  my media folder,
 and was promptly told that I did not have permission to create a folder on that drive  :mad: ...

gksudo nautilus

allowed me to copy to a directory "owned" by root...

And I agree, close that window as soon as you are done, it's risky leaving it open...

and start checking ownership AND permissions to be sure they are as needed.

---

### Post by Miljet on 2009-06-30
> I bought a 750GB , set it up with an external USB device, formatted it to ext3, tried to move my media folder,
and was promptly told that I did not have permission to create a folder on that drive ...

gksudo nautilus

allowed me to copy to a directory "owned" by root...


The only problem with that method is that all the files that you moved into that directory are also now "owned" by root. The only way you can retrieve or play them is with the use of "sudo" or "gksu nautilus".

A better method is to change ownership of the mount point to yourself BEFORE mounting the drive. And don't use "sudo" to mount the drive. That way you own the directory and all the files in it.

Most folks recommend against it, but you can even create a mount point within your home directory and mount the drive there. As long as you don't use "sudo" to create the mount point or actually mount the drive, you automatically own the mount point, the mounted directory, and all the files in it. Actually, it makes more sense to do it that way if you are just using the disk as a large sub-directory to your home directory anyway.

Of course, that all assumes that you are the only user. If you are sharing the computer with other users, then you need to create a new group to assign to the mount point and make sure that all users are a member of that group.

---

### Post by egalvan on 2009-07-01
> **Miljet said:**
> ...**all the files that you moved into that directory are also now "owned" by root**.
 The only way you can retrieve or play them is with the use of "sudo" or "gksu nautilus".

A **better method is to change ownership **of the mount point to yourself BEFORE mounting the drive.
 And don't use "sudo" to mount the drive. That way you own the directory and all the files in it.

Most folks recommend against it, but you can even create a **mount point within your home directory and mount the drive there**.
 As long as you don't use "sudo" to create the mount point or actually mount the drive, you automatically own the mount point, the mounted directory, and all the files in it.
 Actually, it makes more sense to do it that way if you are just using the disk as a large sub-directory to your home directory anyway.
[B]
Of course, that all assumes that [/B]you are the only user. If you are sharing the computer with other users, then **you need to create a new group to assign to the mount point and make sure that all users are a member of that group**.

Yeah, I admit this was not the best way to solve my problem,
but basically it was an example of files that "belong to root" that don't actually "belong to root". Get it?

Your point about changing ownership is valid... 
a much-better method of solving this problem.

Yes, I'm the only user of my machines...

Part of my frustration is that "root" seems to take ownership of drives that were partitioned and formatted on another machine.
Seems pretty Borg-like to me...
But I guess I'll have to look into it further... 
I know I'm doing something out-of-order, or missing a step...

The further point about creating the mount under your home directory...
is that similar to creating a sym-link (in home) to a standard /mnt-based mount?

thanks

---

### Post by Miljet on 2009-07-02
> The further point about creating the mount under your home directory...
is that similar to creating a sym-link (in home) to a standard /mnt-based mount?

No, the standard mount point that the syn-link points to will still have the same permissions. The trick is to either create the mount point without using "sudo", or to change ownership to yourself after it has been created.

---

