---
title: "Ubuntu won't boot and i need to recover my files"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by pammy109 on 2011-02-27
Hi everyone, I'm a bit of a newbie to both this forum and Ubuntu. Today for reasons best known to itself my laptop decided that it was no longer going work with Ubuntu. I'm pretty sure i have the latest version as i updated a few days ago so should be version 10.0?. I am able to put in the live cd and it boots up but i cannot access my hardrive to copy all of my files onto a portable drive for safekeeping and i am getting this message:

Error mounting: mount: wrong fs type, bad option,bad
superblock on/dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog-try
dmesg | tail or so

As i mentioned, i am a total noob and have no idea what i should be doing although i have to admit i've had ubuntu for at least 5-6 months and i am really happy with it but i would prefer not to lose all of my files.

Any help would be appreciated!

Pamela

---

### Post by geoffmcc on 2011-02-27
try adding a -t ext3 (or whatever fs it uses) into your command to mount.

---

### Post by pammy109 on 2011-02-27
> **geoffmcc said:**
> try adding a -t ext3 (or whatever fs it uses) into your command to mount.


As i explained i am a total noob. I do know that i need to go into Terminal but what is the full command line that i should type?

---

### Post by geoffmcc on 2011-02-27
```
mount -t type device dir
```

so if you made a directory in /mnt called restore to mount the drive you would run

```
mount -t ext3 /dev/sda1 /mnt/restore
```


### Edit ###
Installing in virtual box from livecd and it looks like it gets installed as ext4 so after -t use ext4 instead. sorry bout that

---

### Post by ex_isp on 2011-02-27
It may be easier to boot into the live cd and just grab them by using the GUI.

---

### Post by pammy109 on 2011-02-27
> **ex_isp said:**
> It may be easier to boot into the live cd and just grab them by using the GUI.

And how would i go about doing that?

---

### Post by geoffmcc on 2011-02-27
I never had to do it but I glanced at a post that said it wouldn't auto mount the drive that way - but must have been a post about recovering windows partition and i didnt pay enough attention cause i just did it threw virtualbox with no problems.


So just go to places/computer and you should see it there. The one that says filesystem is for live cd - the one that makes reference to the size of the drive is your hard drive

---

### Post by pammy109 on 2011-02-27
> **geoffmcc said:**
> I never had to do it but I glanced at a post that said it wouldn't auto mount the drive that way - but must have been a post about recovering windows partition and i didnt pay enough attention cause i just did it threw virtualbox with no problems.


So just go to places/computer and you should see it there. The one that says filesystem is for live cd - the one that makes reference to the size of the drive is your hard drive


I can see my hard disk in my computer but i am unable to open it and when i try to mount it i get the error message that i wrote in my first post.

I've gone into terminal and written: 

fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008d86f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7114    57136128   83  Linux
/dev/sda2            7114        7296     1466369    5  Extended
/dev/sda5            7114        7296     1466368   82  Linux swap / Solaris

Hope this info gives you guys some insight as to help me out.
Thanks again in advance!

Pamela

---

### Post by geoffmcc on 2011-02-27
may be an unclean filesystem, due to unexpected shutdown.

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

If finds errors and fixes them just restart to see if ubuntu will then boot

Full page @ [http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem]("http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem")

---

### Post by pammy109 on 2011-02-27
> **geoffmcc said:**
> may be an unclean filesystem, due to unexpected shutdown.

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```If finds errors and fixes them just restart to see if ubuntu will then boot

Full page @ [http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem]("http://members.iinet.net.au/%7Eherman546/p10.html#filesystem_check_on_an_ext3_filesystem")

This is what i get now:

/dev/sda1: recovering journal
/dev/sda1: Clearing orphaned inode 1183700 (uid=1000, gid=1000, mode=0100600, size=111001600)
/dev/sda1: Clearing orphaned inode 1976832 (uid=1000, gid=1000, mode=0100644, size=32768)
/dev/sda1: Clearing orphaned inode 1976831 (uid=1000, gid=1000, mode=0100600, size=20120)
/dev/sda1: Clearing orphaned inode 1968711 (uid=1000, gid=1000, mode=0100644, size=32768)
/dev/sda1: Clearing orphaned inode 1968384 (uid=1000, gid=1000, mode=0100600, size=20132)
                                                                               
  254133 inodes used (7.12%)
     335 non-contiguous files (0.1%)
     330 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 223520/783/4
 6019539 blocks used (42.14%)
       0 bad blocks
       1 large file

  182793 regular files
   35124 directories
      59 character device files
      26 block device files
       0 fifos
     428 links
   36063 symbolic links (29672 fast symbolic links)
      59 sockets
--------
  254552 files

---

### Post by geoffmcc on 2011-02-27
> 
/dev/sda1: recovering journal
/dev/sda1: Clearing orphaned inode 1183700 (uid=1000, gid=1000, mode=0100600, size=111001600)
/dev/sda1: Clearing orphaned inode 1976832 (uid=1000, gid=1000, mode=0100644, size=3276
/dev/sda1: Clearing orphaned inode 1976831 (uid=1000, gid=1000, mode=0100600, size=20120)
/dev/sda1: Clearing orphaned inode 1968711 (uid=1000, gid=1000, mode=0100644, size=3276
/dev/sda1: Clearing orphaned inode 1968384 (uid=1000, gid=1000, mode=0100600, size=20132)


I never had this problem but the above makes me think it did in fact fix something. Have you tried to boot your ubuntu without livecd now that did that or mount the drive again?

---

### Post by pammy109 on 2011-02-27
> **geoffmcc said:**
> I never had this problem but the above makes me think it did in fact fix something. Have you tried to boot your ubuntu without livecd now that did that?

Going to try it now. I'll be back shortly to let you know.

---

### Post by pammy109 on 2011-02-27
> **geoffmcc said:**
> I never had this problem but the above makes me think it did in fact fix something. Have you tried to boot your ubuntu without livecd now that did that or mount the drive again?

Thank you so much everyone for your great help. Ubuntu is now working as normal and all my files are still there!
I'm so glad i asked you guys for help, you are all stars.

Pamela

---

### Post by geoffmcc on 2011-02-27
It appears that the laptop did not perform a proper shutdown last was up for whatever reason. Glad we fixed it for ya.

---

