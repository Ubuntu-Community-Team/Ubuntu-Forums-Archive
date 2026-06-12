---
title: "Mounting other filesystem drives"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by keheikev on 2010-07-17
One computer 3 operating systems separate drives. Linux and an unused xp 
partition on one drive and Win 7 on a separate physical drive. For some 
reason the Linux distro Ubuntu 9.10 can't mount the drive without a password 
even though they are not pasword protected. How can I set the permisions so 
that I can mount those drives with ease. These are both internal drives.
:kihei

---

### Post by munkyeetr on 2010-07-17
1) Run the command **blkid** to see your device information
2) Edit the file **/etc/fstab** and add the devices you want mounted at bootup.

Here's some documentation describing fstab options: [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

---

### Post by rbc on 2010-07-17
If you want the partitions mounted at start-up, follow munkyeetr's advice. If you do NOT want them mounted at boot up, but also do not want to have to enter a password when you mount the partitions, follow these instructions:
[http://www.webupd8.org/2009/11/deactivate-password-request-for.html](http://www.webupd8.org/2009/11/deactivate-password-request-for.html)

One change I would make to the instructions is in #1. The author says to use "sudo gedit" to open the file. I would instead use "gksu gedit"

See here for an explanation as to why:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by confused57 on 2010-07-17
Sounds like policykit authorization is requiring your password to grant access permissions:
[http://ubuntuforums.org/showthread.php?t=1308528](http://ubuntuforums.org/showthread.php?t=1308528)

As mentioned above, adding an entry to /etc/fstab would probably be the way to go.

---

### Post by keheikev on 2010-07-18
I think the fstab edit is the way to go as the default in my set up and I presume in most dual boot systems is to mount at start up just don't want to enter a password to mount the disk (s).
:kihei
:popcorn:

---

### Post by Mark Phelps on 2010-07-18
Personally, I would advise AGAINST mounting MS Windows OS partitions automatically at startup -- unless -- you mount them read-only.

Why?

Because, it is absurdly simple to improperly shutdown MS Windows partitions such that they are then rendered unbootable. NTFSFix is then often unable to repair those partitions, and you are left with the situation where you HAVE to boot into MS Windows to run CHKDSK to fix them, but can't because the filesystems are corrupted.

If you configure your FSTAB entries to mount the partitions read-only, you will still have access to the data, and you will avoid the problem of filesystem corruption.

---

### Post by keheikev on 2010-07-18
Hi Mark,
I am thinking more along the lines of being able to read files but I am thinking also of being able to write files like documents and jpegs etc. I really would not  write files to the o/s folders. Are you saying that the risks are too great that Linux could very likely corrupt the boot partition despite taking care to avoid. I could see then why I would only set the partitions permission to read-only. I do have some fairly large non-bootable backup partitions should I make those NTFS partitions read-only if I enable mounting? I had thought Linux supported writing to NTFS fully.
:kihei

---

### Post by Morbius1 on 2010-07-18
This is how the Ubuntu installer will mount ntfs partitions if you had asked it to during the install - have to use manual partition option:

> UUID=DA9056C19056A3B3 /windows/WinXP  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=66E4DC83E4DC56C1 /windows/BACKUP ntfs    defaults,nls=utf8,umask=007,gid=46 0       0What I normally do after the install is modify these a bit. First I get rid of the UUID's because they drive me crazy and replace them with LABEL. But that's another story ;)

The other thing I do is change the umask in the WinXP partition to 227 which will enable all local login users the ability to read but not write to the WinXP partition - - the "2" turns off write.

So I end up with this ( except with LABEL's not UUID's  and I may add a uid=1000 if I need to take possessions of the mount point ):
> UUID=DA9056C19056A3B3 /windows/WinXP  ntfs     defaults,nls=utf8,umask=227,gid=46 0       0
UUID=66E4DC83E4DC56C1 /windows/BACKUP ntfs     defaults,nls=utf8,umask=007,gid=46 0       0This is old-school.

[COLOR=Blue]EDIT: I should explain what this does.[/COLOR]

For both examples the ntfs partitions will mount with owner = root and with read access to all local login users ( the gid = 46 part ). In the case of the BACKUP partition all local login users will also have the ability to write. Everyone else will have no access at all ( a "7" in umask turns off everything ).

---

