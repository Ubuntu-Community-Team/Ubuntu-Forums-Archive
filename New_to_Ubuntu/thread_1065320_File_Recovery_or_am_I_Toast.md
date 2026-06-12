---
title: "File Recovery or am I Toast?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by flyingsolo on 2009-02-09
I suppose this happens to everyone sometime eventually--I was using my laptop on AC supply but it turns out it was my son's Dell charger and not my own (he was away for the weekend and the two got switched) so my computer was effectively on battery and very low.
So, the sad truth is now that I boot up, all my documents (music, video, photos, etc) are 'gone' and my Ubuntu looks like a fresh install except that it has remembered all my installed applications.  Is there any chance I can recover my data?  The installation had a separate /home partition and was running Hardy.  When I open partition editor, it shows /home to be empty.
Hopefully someone can help me get back my stuff.  (Yes, yes-I should have backed up!  I can probably rebuild most of my stuff since I have redundancy across this laptop and a desktop)

---

### Post by jimmy the saint on 2009-02-09
It sounds to me like there is more going on than just a wrong power adapter.  Losing power could make you lose your current work, but not your saved data.  You could try booting from the livecd and going through the filesystem to see if your files are indeed gone, but I don't see how simply having your battery die could cause data loss.

---

### Post by Patsoe on 2009-02-09
Don't do anything with the partition just yet (like reformatting or editing the partition table with fdisk or so). I'm pretty sure that if this is a standard ext2 or ext3 partition, and the only thing that happened is a power cut, you should be able to restore most of it. The only problem: I don't have any real experience with that, so you'll need to wait for someone else to show up here...

edit: btw (just to make my post a tiny bit more useful :)), whatever you do next, I would use dd to make a backup of the damaged partition before you try any recovery of it. This would just take the raw bytes from the partition, so you need a sizeable backup drive.

---

### Post by caljohnsmith on 2009-02-09
I think the first thing I would do would be a file system check on your home partition, and see what it says. You can do the following from your Live CD if you want, but how about doing:
```
sudo fdisk -lu
```
Find which is your home partition sdaX (like sda5 for example), and then do:
```
sudo umount /dev/[COLOR="Blue"]sdaX[/COLOR]
[ "$(mount | grep [COLOR="Blue"]sdaX[/COLOR])" ] || sudo e2fsck -fpv /dev/[COLOR="Blue"]sdaX[/COLOR]

```
Please post the output of all the above commands.

---

### Post by flyingsolo on 2009-02-09
from sudo fdisk -lu:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63761984    31880961    7  HPFS/NTFS
/dev/sda2        63761985    86156594    11197305   83  Linux
/dev/sda3        86156595   304431749   109137577+  83  Linux
/dev/sda4       304431750   312576704     4072477+  82  Linux swap / Solaris

So /home is sda3.  (sda1 is winxp partition I need for work) I haven't proceeded with your part 2 suggestion b/c sudo umount /dev/sda3 returns message that:
umount: /home: device is busy
because I'm using the computer to surf and post here right now and I also get:

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

which scares the *&%#&^ out of me!
Just for example, if I run Amarok now, it gives me ye olde welcome screen and how to start using it.  Another example, FF has none of my bookmarks, passwords etc.  Truecrypt is gone.
<sigh>

---

### Post by caljohnsmith on 2009-02-09
If you want to do file recovery, I think you should immediately stop using that HDD if you want the best chances of recovery. I would recommend booting your Live CD and running those commands from there. Please post the output of the e2fsck command.

---

### Post by flyingsolo on 2009-02-09
OK, I'm doing that now but just to be sure, is part 2 to be entered exactly as above?  That is:
[ "$(mount | grep sda3)" ] || sudo e2fsck -fpv /dev/sda3

after umount of sda3?

---

### Post by Patsoe on 2009-02-09
> **flyingsolo said:**
> OK, I'm doing that now but just to be sure, is part 2 to be entered exactly as above?  That is:
[ "$(mount | grep sda3)" ] || sudo e2fsck -fpv /dev/sda3

after umount of sda3?

Essentially what that says is "only if the mount command tells you that sda3 is not mounted, do the e2fsck".

---

### Post by flyingsolo on 2009-02-09
Nevermind my last post.  I carried on a got the following from sudo e2fsck:

  1642 inodes used (0.01%)
   431 non-contiguous inodes (26.2%)
       # of inodes with ind/dind/tind blocks: 217/4/0
516907 blocks used (1.89%)
     0 bad blocks
     1 large file

  1212 regular files
   413 directories
     0 character device files
     0 block device files
     0 fifos
     0 links
     8 symbolic links (8 fast symbolic links)
     0 sockets
------
  1633 files

I hope this makes sense to someone--greek to me, I'm afraid.
Continued thanks.

---

### Post by caljohnsmith on 2009-02-09
OK, how about next trying:
```
sudo mount /dev/sda3 /mnt && ls -lR /mnt
df -h | grep sda3
```
And please post the output.

---

### Post by flyingsolo on 2009-02-09
OK, output is as follows:

/dev/sda3  103G  347M  97G  1%  /mnt

---

### Post by caljohnsmith on 2009-02-09
You didn't post the output of the first command; is any of the 347 MB of used space any of your files? I would imagine you had a lot more than 347 MB worth of files. If that's the case, I would recommend using "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover your files. You can download and run it from the Live CD with:
```
sudo apt-get install testdisk
sudo photorec
```
Note you will need some other drive/partition that is at least the size of your home partition (103 GB) to save all the recovered files to. After starting photorec with the above command, select your sda HDD and choose "Proceed", "Intel", select your sda3 home partition and choose "Search", "ext2/ext3" as the file system, "Whole", and then you will have an opportunity to show testdisk where to save the recovered files (which should be another drive/partition). Good luck and let us know how it goes.

---

### Post by unutbu on 2009-02-09
You mentioned "Truecrypt is gone." Did you use truecrypt to encrypt your home directory, or a subdirectory, or the whole partition? 

I don't know that much about truecrypt, but if the files you are trying to recover were encrypted, this will definitely influence how you should go about recovering those files, and it might be why they appear to be missing.

---

### Post by flyingsolo on 2009-02-09
I only had a relatively small truecrypt volume with a few GB of stuff in it.  Nothing critical really, I was mainly just 'playing' with truecrypt to see how it worked.

---

### Post by flyingsolo on 2009-02-10
I had to give it a rest for last night but I'm about to go ahead with caljohnsmith's suggestion to use testdisk & photorec but I just tried something else which was to boot into my WinXP partition which fails but returns the message:
Failed to load NTDLR.  Press Ctrl-alt-del to restart.

From Googling this, it seems to be a problem with the BIOS--could this have been disrupted/corrupted b/c of my original power problem with incorrect charger?  I've found some info regarding repairing NTDLR for Windows though I doubt this will help my Ubuntu partition.  Maybe both OS's were affected differently?
Any suggestions are welcome!

---

### Post by Jingle on 2009-02-10
i'd recommend testdisk.. I'm right in the middle of recovering 40gb that vanished this afternoon.  have a nosey down the pages a wee bit and you'll find the link

it's recovering stuff that i've deleted and formatted over several times as well as the stuff I lost today.

---

### Post by Patsoe on 2009-02-10
> **flyingsolo said:**
> I had to give it a rest for last night but I'm about to go ahead with caljohnsmith's suggestion to use testdisk & photorec but I just tried something else which was to boot into my WinXP partition which fails but returns the message:
Failed to load NTDLR.  Press Ctrl-alt-del to restart.

From Googling this, it seems to be a problem with the BIOS--could this have been disrupted/corrupted b/c of my original power problem with incorrect charger?  I've found some info regarding repairing NTDLR for Windows though I doubt this will help my Ubuntu partition.  Maybe both OS's were affected differently?
Any suggestions are welcome!

This is an unlikely combination of errors - why would the Win partition be affected when you were in Ubuntu when the battery died? Did you have your Win file system mounted? (and then still, why would the problem affect the boot files? and why can't ntfs and ext3, both journaling file systems, recover from it?)

Something else might be going on, perhaps the disk is generally dying. If you have a large backup disk at hand, I would really start by backing up the whole disk at block-level, using dd. You can then pester the backup image with recovery attempts. 

If we unluckily misdiagnosed the problem to be related to the battery going flat, and instead your disk is dying, you may not have so many chances left to read from it.

As caljohnsmith said, do all of this from a live-cd.

(And sorry if it turns out I've been worrying you for no reason - better safe than sorry though....)

---

### Post by flyingsolo on 2009-02-10
Just about to start photorec but I have the following choices of directories to recover.  I presume by selecting the top one, I am searching the entire sda3 partition (which is my /home) and it will then give me options of where to write the recovered files?
Do you want to save recovered files in /home/ubuntu ? [Y/N]
Do not choose to write the files to the same partition they were stored on.

To select another directory, use the arrow keys.
drwxr-xr-x   999   999       820 11-Feb-2009 00:51 .
drwxr-xr-x     0     0        60 10-Feb-2009 17:42 ..
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Videos
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Pictures
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Music
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Documents
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Public
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Templates
drwxr-xr-x   999   999       100 10-Feb-2009 17:42 Desktop

BTW, caljohnsmith recommended using photorec but the last post suggested using "dd"--any preference one or the other (and I'm not familiar with dd)

I'm a little confused by photorec.  I chose to recover 'whole disk' and selected filesystem type ext2/ext3 which is when I get the options of where to store the results as listed above.  I was hoping it would allow me to write to an external WD storage drive I have attached via firewire but I don't see the ability to select it.  (the hard drive of the laptop with the problem doesn't have sufficient free space)  I must be missing something here.

---

### Post by Patsoe on 2009-02-10
I'm suggesting to use dd to create a byte-for-byte image of your disk. After doing that, you still need to use other recovery tools on the backup image. It's your data, so do realise the choices are all yours: I would inspect the man pages and other documentation on all the tools, and not just take advice from, say, me because I'm just a guy on the internet.

From your last question I gather you are trying to recover files to the same partition you are hoping to recover. This is not safe.

Consider that your file system has a broken "table of contents" which is why it appears empty. That means the system has no way of knowing where it can safely write new data, and where it might overwrite old data. So really, use a backup disk, and only mount the disk you want to recover with the read-only flag.

(that is "mount -o ro", but again: read man mount, don't take my word for it)

---

### Post by caljohnsmith on 2009-02-10
> **flyingsolo said:**
> ```

[COLOR="Blue"]Do you want to save recovered files in /home/ubuntu[/COLOR] ? [Y/N]
Do not choose to write the files to the same partition they were stored on.

To select another directory, use the arrow keys.
drwxr-xr-x   999   999       820 11-Feb-2009 00:51 .
drwxr-xr-x     0     0        60 10-Feb-2009 17:42 ..
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Videos
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Pictures
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Music
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Documents
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Public
drwxr-xr-x   999   999        60 10-Feb-2009 21:43 Templates
drwxr-xr-x   999   999       100 10-Feb-2009 17:42 Desktop
```

It looks like what you are showing there is when photorec asks you where you want to save your files; if you accept the default which is highlighted in blue, it will save the files to your /home/ubuntu directory on the CD, which is not what you want. What I would recommend is use your up/down arrow keys to select the ".." directory, and that will take you up one level. Again select ".." to get to the root directory "/", go to "/media" and there is probably where your other HDD is mounted.

---

### Post by flyingsolo on 2009-02-24
Reviving this thread after being away...
So, I did run photorec and have generated a long list of 'recup' files (about 34) which contain a lot of fragmented audio files from podcasts as far as I can tell, many .html and .txt files, a bunch of zip files that generate an error when trying to extract (not sure these are ones I had on the drive or would photorec create some to store photos?) but relatively few jpeg files. In fact, the ones I see are mainly thumbnails so not so useful.  One photo I particularly want to recover, I can see only as a thumbnail size version but not the original.
Any advice on interpreting or working with the photorec generated files to make some sense of it all?  
(I don't really care about the podcasts which I can download again if needed; I think mainly I am interested in recovering photos.  BTW, it did very well recovering several home movie video files which seem to be fully intact.)

---

