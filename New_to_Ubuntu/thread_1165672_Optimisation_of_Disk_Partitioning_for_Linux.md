---
title: "Optimisation of Disk Partitioning for Linux"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by bjab on 2009-05-20
Looks like I may have to do a clean install of 9.04 in order to get a standard installation from which I can begin anew.

In the now fondly-remembered days of DOS (I wasn't so fond of it at the time, of course!), I used to partition my hard disk thus: C: DOS operating system only; D: Installed Programs; and E: Data Files.  Thus a re-install or upgrade of the operating system did not necessitate re-installing all the other programs; and an upgrade of an installed program did not risk loss of related data files.  Additionally, migration to a more powerful computer was made very easy.  This simple and obvious approach to system security and stability never seems to have been apprehended by the expensive geeks employed by Microsoft in the development of the dreadful Windows, whose creation of the Registry has made impossible the preservation of installed programs when a Windows "upgrade" is forced upon us, and which does its best to make us keep data files in C drive folders which are then also lost in the said "upgrade" process.

Now I understand that in Linux there is no equivalent to the Windows Registry, that is, each installed program retains its own initiation file(s) in the same way that DOS did.  So my question, as an absolute beginner, to all you knowledgeable and helpful experts out there, is, can I partition my hard disk to make the same separation between the Linux OS, Installed Programs, and Data Files, as I used to under DOS, and with the same benefits of preservation of installed programs and their configurations through a Linux OS upgrade?  (Of course, data files are always  preserved under such a partitioning - as has indeed remained my practice under Windows.)

Hoping someone can help with this basic query ...

---

### Post by Hendronicus on 2009-05-21
This is one those things that could be different for different people. There are many schemes for this. Also, I have to ask; are you dual booting? The usual scheme for just using Linux at home is simply to make one large / (root) partition and a swap partition. Now, in your case that might not be the best idea. The most common scheme for doing what you suggest that I've seen is a small; (about 20 MB or so) /boot partition, then a larger; (about 2/3rds of the drive) / (root) partition, then a smaller; (about 1/3rd of the drive) /home partition, and then an appropriately sized swap partition. This is not exactly what you described, I know, but it is a standard scheme. The reason that I asked if you were dual booting is that on an IDE HD you can only have four primary partitions, so you might have to adjust the scheme for that. If that is the case, I would suggest dropping the /boot partition because you probably don't need it. As I said, there are as many answers to this as there are users, so don't be surprised if someone else has a different idea. Some people reverse the sizes because they have a lot of data, others use more programs than data, and so forth. You have to be the judge of that.

---

### Post by Ravernomina on 2009-05-21
1stly he is asking if he would go 100% linux, 2ndly yes u can do this



first off

the "/" Would be used to mount the OS partition

the "/usr" would be used to mount binaries, compiler libraries and user applications

the "/home" for your files and documents 

Their your partition dreams are back my friend :) welcome to Linux ):P



P.S. if u need any more info on mount points see [here]("http://www.comptechdoc.org/os/linux/manual1/mountpoints.html")

---

### Post by nhasian on 2009-05-21
Hello bjab,

May I recommend you setup your partitions with these filesystems:

/ EXT4
/home EXT3
/swap SWAP

and if you want a separate data directory for your videos/mp3s/pictures then:

/data EXT4

---

### Post by Vunutus on 2009-05-21
> **nhasian said:**
> Hello bjab,

May I recommend you setup your partitions with these filesystems:

/ EXT4
/home EXT3
/swap SWAP

and if you want a separate data directory for your videos/mp3s/pictures then:

/data EXT4

What's the reason for using ext4 on root and data but not home?

---

### Post by nhasian on 2009-05-21
good question!  when ext4 first entered the stable branch of the linux kernel and people started using it, they sometimes ran into data corruption on their ext4 volumes if they lost power or locked up.  at first ext4 was blamed, but in fact it was working fine.  gnome and kde windows managers were not closing their configuration files properly after writing to them which caused the data loss.  so until they are fixed, either user EXT3 for your /home directory or dont run out of power :)

> **Vunutus said:**
> What's the reason for using ext4 on root and data but not home?

---

### Post by Ravernomina on 2009-05-21
o really gnome locked up on me all my data did not corrupt and i was torrenting items as well and it still worked :l personaly they should look in the lost+found folders to get all the their data back -_-


[EXT4 only does this when u over work the sytem (to many read + wrights at once) will cause this result, and u should always have some short of a data back up i recommend a removable hard drive or a army of blank dvds/cds :P]

---

### Post by scorp123 on 2009-05-21
> **bjab said:**
>  Thus a re-install or upgrade of the operating system did not necessitate re-installing all the other programs; Exactly.

> **bjab said:**
>  can I partition my hard disk to make the same separation between the Linux OS, Installed Programs, and Data Files Actually, such partitioning used to be **_*THE* standard_** on UNIX-like operating systems!! It's only that with the advent of distros such as Ubuntu they tried to make things "noob-friendly" (no insult intended here) and they dumbed-down the installer to only go for one single root "/" partition per default (thus keeping things simple for newcomers... too simple maybe?) instead of enforcing the classical partitioning scheme (which some other operating systems that don't care about catering to newcomers still do).

> **bjab said:**
>  Hoping someone can help with this basic query ... Please see these posts:
[http://ubuntuforums.org/showpost.php?p=4251551&postcount=3](http://ubuntuforums.org/showpost.php?p=4251551&postcount=3)
[http://ubuntuforums.org/showpost.php?p=4252055&postcount=7](http://ubuntuforums.org/showpost.php?p=4252055&postcount=7)

My current partitioning on my main Linux desktop PC looks like this:

```
 > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             130M   18M  105M  15% /boot
/dev/sda5             1.9G  157M  1.8G   9% /
/dev/sda6             7.7G  4.3G  3.4G  56% /usr
/dev/sda7             3.9G  925M  3.0G  24% /var
/dev/sda8             7.7G  222M  7.5G   3% /opt
/dev/sda9             7.7G  4.3M  7.7G   1% /tmp
/dev/sda10            388G  100G  288G  26% /home
/dev/sdb1             597G  527G   71G  89% /data

```

My /boot is Ext3, the rest is XFS. As I regularly deal with really large files I found XFS to be best for this. Not shown here are my Solaris filesystems ... those are ZFS.

.
.

---

