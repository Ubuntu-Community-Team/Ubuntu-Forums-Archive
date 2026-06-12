---
title: "Computer crashed--can I access Windows docs  through Ubuntu?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by ariapace on 2010-03-01
My Windows XP computer crashed, possibly from a virus, and I can't boot it up in Windows.  All that I can access is the BIOS.  However, Ubuntu works on the computer.  I'm using it right now from the CD.  Is there any way that I can access my Windows documents through Ubuntu?

(I'm fed up with Windows, and I want to use Ubuntu from now on, but would like to access some documents that weren't backed up.)

---

### Post by zeroseven0183 on 2010-03-01
Yes, you can access the files using the LiveCD. Can you check if the partition where your Windows is installed and where the data are stored are detected? Click Places and select Computer then browse the drives to see where your documents are.

I suggest you start backing up your data before installing Ubuntu.

---

### Post by ariapace on 2010-03-01
I went to Places / Computer, but I don't think it's detecting the Windows partitions.  It lists CD/DVD drive, Floppy Drive, USB drives, and "File System," which seems to be Ubuntu files.

---

### Post by zeroseven0183 on 2010-03-01
Hmmmm... That's strange. While running in LiveCD you should have at least see another icon which say ##.# GB Media (depends on how large your Windows Partition is) together with the CD/DVD Drive, Floppy Drive, Filesystem, etc.

Is the hard drive still detected in the BIOS?

---

### Post by ndefontenay on 2010-03-01
I have to echo what has been said just above. You should see at least the windows partition. It's usually called "OS" (I don't know why it's rather confusing). If you don't, you should make sure your hard disk is still working. You can run linux from the live CD because it doesn't require a Hard disk at that point.

It looks like your computer is not working because your HD failed. Check it.

---

### Post by ariapace on 2010-03-01
I don't see where the hard drive is detected in the BIOS, but I'm not really that knowledgeable about the BIOS.  What I can get into when I turn the computer on and keep pressing F1 is the BIOS Setup Utility.

Maybe I should just try to install Ubuntu and see if the hard drive works?

---

### Post by switch10 on 2010-03-01
if you open your terminal, and type:
```
 sudo fdisk -l 
```
it will list the disks, and partitions.

look for one that says NTFS, that is your Windows install.

to mount the (all) file system(s) type this;

```
 sudo mount -a 
```

the partition will show up on your desktop

Good Luck!

Dave

---

### Post by sandyd on 2010-03-01
go to system -> administration -> gparted.

if your disk is NOT listed there, consider disconnecting your hard drive, sticking it in a freezer-proof bag, and chucking it in the freezer. bring it out after a while and try again.
(and yes, im serious)

if it shows up, install testdisk (Accessories -> Terminal)
type in
```

sudo apt-get install testdisk
sudo testdisk

```
testdisk can recover the files in your HD for you if the HD is still partially accessable.

---

### Post by lavinog on 2010-03-01
> **carlee said:**
> go to system -> administration -> gparted.

if your disk is NOT listed there, consider disconnecting your hard drive, sticking it in a freezer-proof bag, and chucking it in the freezer. bring it out after a while and try again.
(and yes, im serious)


I don't think that will work if the drive is not being detected in bios...that is more of a crashed head trick.

@OP: What is the model number and manufacturer of the drive (look at label)
There were a couple of seagate drives with a bad firmware that would cause the drive firmware to segfault after a while (mine occured after 8 months of use) which prevents them from being detected by bios.
If this is the case, there are ways to recover the data...but it requires some serious hacking.

here is some information about the issue I am describing:
[http://www.msfn.org/board/topic/128807-the-solution-for-seagate-720011-hdds/?](http://www.msfn.org/board/topic/128807-the-solution-for-seagate-720011-hdds/?)

---

### Post by koba101 on 2010-03-01
what error does it display if you try to boot windows?

---

### Post by zeroseven0183 on 2010-03-02
I wonder what happened to the hard drive?

---

### Post by ariapace on 2010-03-04
Thanks to everyone for your suggestions!  It appears to be at least a hard drive problem, and maybe more.  It's an HP Pavillion a650e.  It's got 2 hard drives, and they are in a mirror array or something.  When the computer first crashed and I got into the BIOS I may have messed up something too.  :(

I decided to try to clean install Ubuntu, and it worked up to about 95%, and then I got a message saying the GRUB thing wouldn't install, and therefore the computer would never boot up.

So I may just give up on it and give it to a friend to see if he can do something with it.  I've been thinking for a while now of getting a Mac because I want to use Logic for composing music.

However... in the meantime I installed Ubuntu on an old laptop from my office, and I really like it!  I've been wanting to use a Linux program for a long time, and I find Ubuntu so easy to use, and graphically really beautiful.  I'm having a lot of fun exploring it.

---

