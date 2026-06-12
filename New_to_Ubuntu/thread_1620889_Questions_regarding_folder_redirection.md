---
title: "Questions regarding folder redirection"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by acag on 2010-11-13
I am a newbie that is preparing to install Ubuntu 10.04 Desktop version  on a PC with two internal hard drives. Lucid will be the only OS on this  PC. I have the following items where I need assistance:

1) I  want to set up my system so that a reinstall or upgrade of the OS will  not impact my user configs or data. I am guessing that the best way to  do this is to separate /home from the OS by putting the OS and SWAP on  drive #1 and /home on drive #2. I would like to separate them at install  time if possible. Is this the best way to minimize the impact of a  reinstall or upgrade? If not, what do you suggest? If so, how do I  accomplish this?

2) My wife and I will have separate IDs on this  PC. I would like to set them up so that our individual Pictures &  Videos folders point to the same location. This would allow either of us  to download pictures or videos from our cameras and they would be  available to both IDs just by selecting our individual folders from our  Places menu. This would prevent duplication and simplify backups. How do  I accomplish this?

3) I am considering a future purchase of a  NAS unit. When this becomes a reality, how will I move the pictures and  videos pointers that were created in step 2 above to the NAS unit?

As  I stated before, I am a newbie who knows what they want but has no idea  how to accomplish it. Any assistance that you can provide will be of  great help.

---

### Post by jrev on 2010-11-13
The simplest is to get your pictures on your Documents and let your wife permission to access this folder

---

### Post by oldfred on 2010-11-13
My wife & I just have my login. But I saved a few links. You need to create a group and assign you & your wife to that group. Then permissions control whether group has access. I believe bindfs is an alternative way.

I also like to do clean installs and if you have no data in the system partition it only needs to be 10-20GB. I create several / partitions and keep my last install in case I need an old system setting, my current install, and another for testing the beta or before to see how I like the next install.

The /home will have all the user settings for you & your wife.


Shared users using bindfs:
[http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by sisco311 on 2010-11-13
If you choose bindfs, take a look at:
[thread=1460472]HowTo: Create a shared directory for local users (with bindfs)[/thread]

But, before that, I think, you should learn how [Unix/Linux file permissions]("http://content.hccfl.edu/pollock/aunix1/filepermissions.htm") work.

---

