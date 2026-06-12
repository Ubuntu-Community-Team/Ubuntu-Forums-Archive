---
title: "cannot copy from desktop to other drives"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by soona86 on 2010-05-24
Hi,
I can't copy files on the desktop to other drives like D or so..
When I right-click on a space in any drive D folder, I see that I can't create files or paste files.
It's like I'm not the admin for these drives, but I can copy files on desktop (on the system drive) = I am the admin on it.
So, how can I enable the admin authorisations for me on other drives?
any help? :)
thanks in advance

---

### Post by SRST Technologies on 2010-05-24
What kind of Linux are you running that uses a D drive?

---

### Post by anarchywolf46 on 2010-05-24
Um... you need to use a cd burner to burn data to the disk, you can't just copy and paste I don't think. Open up like... brasearo or amarok or something of the sorts and use it to copy the data onto a cd.

If it's a USB flashdrive or external drive, it should be as simple as copying files.

I'm going under the assumption D drive is your CD drive.

---

### Post by SRST Technologies on 2010-05-24
There is no need to burn a CD just to copy from one disk partition or drive to another.  None.  No reason whatsoever.

---

### Post by soona86 on 2010-05-24
It's Xubuntu 8.04
I think my problem is about admin permissions..
I just did a (sudo mv) command..the file did move but it can't be read on D.
also, other files on D (when I right-click them) I see that I can copy them but I can't rename nor cute nor delete them.

---

### Post by SRST Technologies on 2010-05-24
Ok, let's start from scratch.

What is D?  Is it a Windows drive or is a mount point you called D?

---

### Post by soona86 on 2010-05-24
> **anarchywolf46 said:**
> Um... you need to use a cd burner to burn data to the disk, you can't just copy and paste I don't think. Open up like... brasearo or amarok or something of the sorts and use it to copy the data onto a cd.

If it's a USB flashdrive or external drive, it should be as simple as copying files.

I'm going under the assumption D drive is your CD drive.

oh no my CD drive is F already :) thanks anyway :)
sorry if I wasn't clear..I meant from a hard disk drive to another

---

### Post by soona86 on 2010-05-24
> **SRST Technologies said:**
> Ok, let's start from scratch.

What is D?  Is it a Windows drive or is a mount point you called D?

windows drive? does it mean the drive that has the system on it? (usually is C)?
or it means something like a drive that appears only on windows or something like that?

well, in my case I meant D as a drive I mounted on Xubuntu (D on windows). and namely on Xubuntu it's not called D; it's name is (sda2)

---

### Post by anarchywolf46 on 2010-05-24
> **SRST Technologies said:**
> There is no need to burn a CD just to copy from one disk partition or drive to another.  None.  No reason whatsoever.
As I said, I was going under the assumption it was a CD drive, the D drive...

Maybe check the file permissions on both the files you want to copy as well as the drive you wish to copy to?

Edit: Just read the last thing you posted... maybe mount the partition in xubuntu and then move the files from there? Just guessing from [http://ubuntuforums.org/showthread.php?t=198041](http://ubuntuforums.org/showthread.php?t=198041) this thread.

---

### Post by soona86 on 2010-05-24
> **anarchywolf46 said:**
> As I said, I was going under the assumption it was a CD drive, the D drive...

Maybe check the file permissions on both the files you want to copy as well as the drive you wish to copy to?

how can i check and what should i do after checking? :)
i mean as i understood; the other drive my permissions are deactivated (rightclick>properties>permissions) it's all deactivated & under (access) it's (read only) there are 2 accesses one is read&write and the other is read only. i hope my information is understandable :oops:

---

### Post by soona86 on 2010-05-24
my drives are auto mounted already but the point is about permissions
how can i change permissions ??? i mean like (make myself a "root" user) or admin or whatever is that called :D

---

### Post by bigsmitty64 on 2010-05-24
Type this in terminal

```
gksudo nautilus
```

then enter your password, then you should be good to go.....I think thats what you're looking for?   :)

---

### Post by SRST Technologies on 2010-05-24
> **soona86 said:**
> windows drive? does it mean the drive that has the system on it? (usually is C)?
or it means something like a drive that appears only on windows or something like that?

well, in my case I meant D as a drive I mounted on Xubuntu (D on windows). and namely on Xubuntu it's not called D; it's name is (sda2)

In Linux, there is no D: or C: or any drive letter.  Linux uses mount points that you define (there's a few the system automatically makes, like /) and the top of the file system is called /

You can mount a partition anywhere you want.  sda2 is probably your dual booted Linux installation, but sda2 just means the first disk, second partition.  You can mount a partition and a filesystem anywhere you want.  What we need to know now is the filesystem and partition of the other drive you were talking about so we can assist you further.

---

### Post by SRST Technologies on 2010-05-24
> **bigsmitty64 said:**
> Type this in terminal

```
gksudo nautilus
```

then enter your password, then you should be good to go.....I think thats what you're looking for?   :)

DO NOT DO THIS EVER FOR FILE TRANSFERS!

If you do, the owner of the file you transferred will become root and you will not be able to edit it or delete it without major problems.

---

### Post by anarchywolf46 on 2010-05-24
> **soona86 said:**
> my drives are auto mounted already but the point is about permissions
how can i change permissions ??? i mean like (make myself a "root" user) or admin or whatever is that called :D
As far as changing permissions you would use
```
sudo chmod
```
followed by the permissions and file you wish to change. However, you cannot do this on a Windows partition if I remember correctly. From my searching, it is best to do the file transfers from the Linux side, it should be able to support NTFS, which is most likely what you are using.

To quote "If you have a dual-boot machine and you're after files from one to the other, do it from the Linux side. [URL="http://www.astahost.com/info.php/copy-file-amp-folders-linux-windows_t18662.html#"][COLOR=#009600][COLOR=#009600 ! important][FONT=Verdana][COLOR=#009600 ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]Linux can read anything (unencrypted) that Windows can write. It is easiest to keep track of things if you create a separate data partition that is accessible to both operating systems. That reduces the chance that you may accidentally damage something in the Windows operating system."

So I would say mount it in Linux and transfer files from there, or create another partition for the files, or use a flash drive to move files between each other. That's the best I can suggest from my findings.

---

### Post by SRST Technologies on 2010-05-24
I'm having difficulty in finding the part in this thread where he said he had an NTFS partition mounted to his Ubuntu install, anarchywolf46.  Please stop giving advice for things that have not been defined yet.

---

### Post by DrDevice on 2010-05-25
Hello everybody.  Just the good Doctor putting in his two cent's worth.  From the sounds of this, he's auto-mounting his partitions, very nice.  We need to know what his setup looks like.  And so, to you, dear Soona86, I ask you to do the following.

Press Alt-F2, then in that box type```
gedit /etc/fstab
```

You should be given a window with a bunch of information in it.  This tells us what Ubuntu is setting your auto-mounted drives up with as far as permissions, etc.  Just copy and paste that into a reply here.  Please make sure to use the CODE tags around what you paste to make it easy for us to read.  (Code tags are found on the toolbar, button has a '#' on it)

Once we have that, we can probably find the source of the problem and get it fixed toot-sweet.

---

### Post by anarchywolf46 on 2010-05-25
> **SRST Technologies said:**
> I'm having difficulty in finding the part in this thread where he said he had an NTFS partition mounted to his Ubuntu install, anarchywolf46.  Please stop giving advice for things that have not been defined yet.
I think you missread me making an assumption of it probably being NTFS since that is what is commonly used. It could be FAT32 which is also supported by Linux, but FAT32 has security issues. It using NTFS has little bearing on my actual post, the mention of NTFS was just me pointing out that Linux supports NTFS now. I did not say for sure it was NTFS nor did I say it needs to be NTFS. The file system on Windows will be supported in Linux. I'm sorry for putting extra information in my post that confused you, did not mean to make you re-read the post looking for some extra information I added.

---

### Post by SRST Technologies on 2010-05-25
Do you even read what you type, anarchywolf?

---

