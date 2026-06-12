---
title: "I created a backup. Simple query on how to restore"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by dgg9879 on 2008-12-19
Using the advice in this link I was able to create a backup from the command line. I put it on my external drive.


[http://www.zimbio.com/the+ubuntu+guy/articles/47/Backup+Ubuntu+Easy+Way+Command+Line](http://www.zimbio.com/the+ubuntu+guy/articles/47/Backup+Ubuntu+Easy+Way+Command+Line)

The link provides the command to restore but it says the backup must be transferred to the root directory first. Please tell me how I do that?

I know the external drive where the backup is stored is called Elements and is denoted by the letter I (in windows) but have no idea what Ubuntu sees it as.

I want to be able to make sure I get the restore right if I ever use it because otherwise I could accidentally wipe over something else.

---

### Post by jerome1232 on 2008-12-19
You can to do it without moving to the root directory actually.

```
sudo tar xvpfz backup.tgz -C /
```

a breakdown of that command

sudo - assume root privileges

-x - extract from an archive

-v - be verbose and tell you what is being extracted (you can add up to 3 v's total for full verbosity

-p - perserve permissions, actually not needed when ran as root (using sudo) since it's default behavior for the root user

-f - extract to/from a file instead of standard input

-z - use gunzip/gzip for compression/decompression of the archive

and the last option -C / tells it to switch to the root directory (/) before begining the extraction.

---

### Post by dgg9879 on 2008-12-19
> **jerome1232 said:**
> You can to do it without moving to the root directory actually.

```
sudo tar xvpfz backup.tgz -C /
```

a breakdown of that command

sudo - assume root privileges

-x - extract from an archive

-v - be verbose and tell you what is being extracted (you can add up to 3 v's total for full verbosity

-p - perserve permissions, actually not needed when ran as root (using sudo) since it's default behavior for the root user

-f - extract to/from a file instead of standard input

-z - use gunzip/gzip for compression/decompression of the archive

and the last option -C / tells it to switch to the root directory (/) before begining the extraction.
My concern is not so much about whether I am in the root directory but how to transfer the backup from the external drive to the root directory so I can restore. Otherwise, how will ubuntu find it?

To be in root directory all I need to do is: cd /

Also I backed it up on CD in windows and it said the size was only 2k. I know it is compressed but that still seems way to small.

---

### Post by linux_tech on 2008-12-19
It may also be helpful to see what files are in the backup volume.  Use the --list or -t option. 
ie.
tar -tvf file.tar

---

### Post by logos34 on 2008-12-19
jerome1232 answered your question clearly, I thought

let's say linux crashes and you need to restore: you'd boot from the live cd, mount both the linux root and external disk partitions (say, at '/media/ubuntu' and '/media/backup'), cd into the latter's directory containing the backup.tgz, then run that command--it will unzip and untar the archive to / (root) in a single action. Actually it would look like this:

sudo tar xvpfz backup.tgz -C /media/ubuntu

---

### Post by prshah on 2008-12-20
> **dgg9879 said:**
> 
Also I backed it up on CD in windows and it said the size was only 2k. I know it is compressed but that still seems way to small.

Yes too small. Also, the backup method shown in the link creates an "ububackup.tgz" file that you should copy wherever you want; another partition / CD, etc. 2Kb is too small, you've done something wrong, better you create another backup file before you try to restore this.

As for restore, the post by jerome1232 earlier in this thread gives you all the details. (Well explained, btw).

---

### Post by dgg9879 on 2008-12-20
If I take Jerome1232's advice do I have to be in the drive where the backup is stored for it to work or will ubuntu still find it wherever it is simply from the file name? If I need to be in the drive where the backup is stored then I need to be able to find out how to do this, including how to find out what the "name" of this dtive is in ubuntu (the same drive letter as windows?).

Also it would be good to know the approximate size of what a compressed ubuntu backup should be.

My Ubuntu partition is 30gb and I installed quite a few things. Is it possible there is not enough room to store the backup? If there is not enough room then could I simply increase the partition size the same way I originally created the partition (with the Ubuntu installation disk)?

I'm thinking maybe this is the reason my backup was so small. Also, how long should the backup take with a Core 2 Duo processor?

---

### Post by jerome1232 on 2008-12-20
> **dgg9879 said:**
> If I take Jerome1232's advice do I have to be in the drive where the backup is stored for it to work or will ubuntu still find it wherever it is simply from the file name? If I need to be in the drive where the backup is stored then I need to be able to find out how to do this, including how to find out what the "name" of this dtive is in ubuntu (the same drive letter as windows?).

Well some of this is situational. 

When you open a terminal you are at your home directory (/home/username aka ~/)

If you poped open a terminal and immediately ran the command posted on that site you would then have a backup file located at ~/ububackup.tgz

If you attach a removable disk to the  system the system will detect that and mount it under /media, usually as disk (and count up for each disk you attach) if the filesystem has a label it will mount at /media/labelname, at any rate you can type ls /media and you should be able to figure out the mount point. Also you can type "mount" all by itself to get a listing of where all attached drives are mounted at.

So let's say you need to restore and you already copied your file to a removable disk, I would boot to a live cd, mount your ubuntu system to /media/root, attach your storage and restore like this, this command can be run from any directory since it has absolute paths, so it tells the command where to look for the files.

I leave out the -p because as I said when ran as root it's not needed
```
sudo tar xvzf [COLOR="Red"]/media/disk/ububackup.tgz[/COLOR] -C [COLOR="Red"]/media/root[/COLOR]
```

Now this isn't a copy/paste command since the parts highlighted in red will differ depending on where you store your backup and where you mounted your filesystem at.

---

### Post by logos34 on 2008-12-20
> **dgg9879 said:**
> If I take Jerome1232's advice do I have to be in the drive where the backup is stored for it to work or will ubuntu still find it wherever it is simply from the file name? If I need to be in the drive where the backup is stored then I need to be able to find out how to do this, including how to find out what the "name" of this dtive is in ubuntu (the same drive letter as windows?).

no you don't to be in the drive where the backup is stored, nor in /, but either makes the pathways shorter and easier to manage.  Either cd into the backup drive and then use the '-C /path/to/root' option, or extract the archive from inside / as your working directory:

cd /path/to/root

sudo tar xzvpf /path/to/backup.tgz

It will unzip and untar the .tgz file right there. 

sudo fdisk -l 

will list all storage devices

like I said, if you need to restore linux root from backup hard disk or CD, you'd mount the volumes on the live CD, then change directory (to either source or /) and run the command

> Also it would be good to know the approximate size of what a compressed ubuntu backup should be.

I regularly tar and gzip my /home (~9 gb) and I get a .tgz ~5 gb. bzip2 is about 15% better than gzip (but way slower).  7zip is the best, IIRC


>  If there is not enough room then could I simply increase the partition size the same way I originally created the partition (with the Ubuntu installation disk)?

yes
> 
how long should the backup take with a Core 2 Duo processor?

I have a wimpy 'Sempy (Sempron 2.0 GHz) and it takes me ~30 min, just to give you a rough benchmark

---

### Post by mapes12 on 2008-12-20
> I know the external drive where the backup is stored is called Elements and is denoted by the letter I (in windows) but have no idea what Ubuntu sees it as.Some observations:

1. Have you formatted this partition to ext3 for linux file storage?
2.The drive letter that windows sees this partition is irrelevant. You need to establish how Linux sees the partition/drive. Plug it in and go to Terminal: ```
fdisk -l
```Post the output on this thread. You may have to "mount" it. If you can see it but not access the files then post back for further help in mounting it.
3. The HowTo website you refer to has some --exclude commands missing which may result in a failed restore. I can post more detail on this once we know the answers to 1 & 2 above.

---

### Post by dgg9879 on 2008-12-20
Thanks for all your help. I actually found this excellent guide on how to use partimage to backup in these forums. I tried it and it seems to have worked. I guess I won't know for sure though until I have to perform a restore. I think I will have to find a good book on ubuntu/linux on amazon to work out how to use the command line.

[http://ubuntuforums.org/showthread.php?t=226402](http://ubuntuforums.org/showthread.php?t=226402)

---

