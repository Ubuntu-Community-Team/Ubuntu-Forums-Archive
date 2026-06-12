---
title: "hard drive transfer"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by normann on 2010-02-19
hi i,m learning. my computor is old and starting to give problems.asked in store if i bought new would they transfer my hard drives to new machine.no problem .after 2 hours they said could not be done.waiting in anticipation

---

### Post by Sef on 2010-02-19
If you have a usb key or a external hard drive,  I would use a LIve CD and transfer the data to it and then to your new hard drive.   For the Live CD, [Knoppix]("http://knoppix.com") is very good.

---

### Post by grahams on 2010-02-19
Not sure what you are trying to transfer but the dd command is commonly used for image copying disks. 

Clonezilla (clonezilla.org), is a nice bootable tool for this.

---

### Post by nhasian on 2010-02-19
do *not* put your old hard drives in a new computer.  all you will end up doing is slowing down your new computer.  I'm sure the new computer's hard disk is leaps and bounds larger and faster than your old drives.  just copy whatever data you need to the new computer.  the best way would be with a usb thumbdrive or usb external hard disk, but you could also network the two computers as well to do the file transfers.

---

### Post by normann on 2010-02-19
> **nhasian said:**
> do *not* put your old hard drives in a new computer.  all you will end up doing is slowing down your new computer.  I'm sure the new computer's hard disk is leaps and bounds larger and faster than your old drives.  just copy whatever data you need to the new computer.  the best way would be with a usb thumbdrive or usb external hard disk, but you could also network the two computers as well to do the file transfers.

thanks.new computer only has windows 7 start.and i wanted to carry on with ubuntu that i,m using

---

### Post by halitech on 2010-02-19
do a fresh install of Ubuntu and then use a thumb drive to start copying files over. Or if you have alot, share a folder and copy them that way.

---

### Post by normann on 2010-02-19
> **grahams said:**
> Not sure what you are trying to transfer but the dd command is commonly used for image copying disks. 

Clonezilla (clonezilla.org), is a nice bootable tool for this.
sorry not sure what dd is.new computer has windows 7 start .i wanted to transfer ubuntu

---

### Post by 2hot6ft2 on 2010-02-19
> **normann said:**
> sorry not sure what dd is.new computer has windows 7 start .i wanted to transfer ubuntu
dd stands for (data dump) and is a command line tool that can clone data from one drive to another.
You should really do a fresh install on a new pc since the hardware will be different and it may not work like you're thinking.

If you want to learn more about dd and it's use look here
[Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

I just made a post last night about cloning a drive with dd here
[Cloning a drive with dd]("http://ubuntuforums.org/showpost.php?p=8849042&postcount=3")

But again like everyone is telling you, you should do a fresh install instead. It will wipe out everything on the new pc's drive.

---

### Post by undecim on 2010-02-19
> **normann said:**
> hi i,m learning. my computor is old and starting to give problems.asked in store if i bought new would they transfer my hard drives to new machine.no problem .after 2 hours they said could not be done.waiting in anticipation

They were probably trying to transfer the files but didn't know how to access Ubuntu's filesystem.

If you can still use your old computer, you can log in, and copy your home directory from the old computer to the new computer using a network connection and shared folder, or an external USB drive.

Copying your home folder like I described above will save all your user settings if you put the files back in the same place on the new system.

However, you still need to reinstall any extra programs you installed to your old system. A useful guide for automating this process is [http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by normann on 2010-02-24
> **nhasian said:**
> do *not* put your old hard drives in a new computer.  all you will end up doing is slowing down your new computer.  I'm sure the new computer's hard disk is leaps and bounds larger and faster than your old drives.  just copy whatever data you need to the new computer.  the best way would be with a usb thumbdrive or usb external hard disk, but you could also network the two computers as well to do the file transfers.

thanks for advice. i,ll leave old drives in old computer.now, when i put ubuntu on my new computer will i get new name and password.:)

---

### Post by normann on 2010-02-24
> **2hot6ft2 said:**
> dd stands for (data dump) and is a command line tool that can clone data from one drive to another.
You should really do a fresh install on a new pc since the hardware will be different and it may not work like you're thinking.

If you want to learn more about dd and it's use look here
[Learn the DD command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

I just made a post last night about cloning a drive with dd here
[Cloning a drive with dd]("http://ubuntuforums.org/showpost.php?p=8849042&postcount=3")

But again like everyone is telling you, you should do a fresh install instead. It will wipe out everything on the new pc's drive.
thanks again. going to do a fresh install

---

### Post by JKyleOKC on 2010-02-25
> **normann said:**
> when i put ubuntu on my new computer will i get new name and password.:)During the install you'll be asked for the name to use, and the password. If you use the same ones as on the old machine, they'll be the same on both machines. I have five machines in my home office, all running xubuntu, and all five have the same user name and password. It's never caused any problems, and makes life much simpler when moving from one to another...

---

### Post by Blaze1024 on 2010-03-03
> **grahams said:**
> Not sure what you are trying to transfer but the dd command is commonly used for image copying disks. 

Clonezilla (clonezilla.org), is a nice bootable tool for this.

dd or Data Dump is a very old utility. dd was intended to make tape backups and not transfer partions to new drives. So it's not really the recommended method for transferring hard drive partitions to a new hard drive.

The problem is dd makes an exact duplicate of your partion. This duplicate includes hardware level system info that should not be transfered to a new hard drive. 

 For example any bad blocks that were flagged when the Hard drive was formatted. If you use dd to move a partition to a new HD then dd will mark the same physical blocks as bad on the new drive (very BAD!!)

  It's best to format the new drive and install your files using a file level backup utility

---

### Post by Easy Limits on 2010-03-03
You could use Giver to move files from one computer to another over your network.  You can find Giver in the Ubuntu Software Center.  It works great.

---

