---
title: "Best File System for Ubuntu and Windows"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by dr.silly on 2008-12-17
I need to create a partition which will need read/write access in both Windows and in Ubuntu. What is the best file system for this?

---

### Post by SuperSonic4 on 2008-12-17
ext3 - more stable, has journaling but no native windows support and I find the fs driver to be patchy

ntfs - windows native, not foss and dependent on reverse engineering. Although ntfs-config can automount it on boot

---

### Post by xjcannonx on 2008-12-17
well from my understanding, windows has a hard time reading/writing to a lot of other file systems besides NTFS or fat unless you buy some additional software, but you can just use NTFS and install ntfsprogs for ubuntu, I believe the current update is in the repo's?

---

### Post by theozzlives on 2008-12-17
> **dr.silly said:**
> I need to create a partition which will need read/write access in both Windows and in Ubuntu. What is the best file system for this?

ext3 use Ext2Fsd to access it in Windows.

---

### Post by dr.silly on 2008-12-17
Ideally something really simple for setup. All I really need to do is use it for /home.

---

### Post by dr.silly on 2008-12-17
Windows and Linux both do fine with FAT, right?

---

### Post by cariboo on 2008-12-17
Windows and Linux both do fine with NTFS, if you use a vfat file system you will be limited to a 4Gb file size.

Jim

---

### Post by nhasian on 2008-12-17
just use the default EXT3 partitions for ubuntu.  then install EXT2IFS in windows to read/write the EXT3 partitions.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jenkinbr on 2008-12-17
> **dr.silly said:**
> Ideally something really simple for setup. All I really need to do is use it for /home.

Due to the permissions and security issues, /home has to be on a filesystem that uses linux file permissions.  therefore, you will most likely want to use EXT3 and install Ext2FS in windows.

---

### Post by halitech on 2008-12-17
> **dr.silly said:**
> Ideally something really simple for setup. All I really need to do is use it for /home.

If you want it for you /home partition, you have no choice but to use a Linux file system. If you want storage, fat32 would give you the least amount of headaches and unless you plan on storing single files over 4gig then you shouldn't have a problem with creating a seperate /storage partition in fat32.

---

### Post by dr.silly on 2008-12-17
I was really looking for native support but I looked at the ext2ifs software and I think I may try that out first. Has any one had any bad luck with that software?

---

### Post by jenkinbr on 2008-12-17
No negative comments on my end - The only thing to watch out for is to try not to name files that only differ in terms of capitalization - windows will only do something with one of the files, but that is a windows issue.

---

### Post by dr.silly on 2008-12-18
ok I installed ext2ifs but I ran into a problem and the mountdiag.exe told me this:

```
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.

```

And reformating is something I really don't want to do.

---

### Post by stchman on 2008-12-18
> **dr.silly said:**
> I need to create a partition which will need read/write access in both Windows and in Ubuntu. What is the best file system for this?

I use NTFS for shared partitions.  The ntfs-3g has worked very well for me and I have never had any data corruption.  Ubuntu and Windows also natively read/write for FAT32 partitions.  If you never have a file over 4GB then FAT32 is a good option.

BTW, ntfs-3g is default install on Ubuntu since Gutsy I believe.  Also NEVER use your /home or other Linux partitions as a shared partition, likewise DO NOT use ntfs-3g on your C:\ partition.  You are asking for trouble.  Make a separate partition for shared data.  There is never a need to write to C:\ in Windows from Linux or / in Linux from Windows.  The C:\ and / contain important system files that if inadvertently erased can cause that OS to be unusable.

---

### Post by jenkinbr on 2008-12-18
> **stchman said:**
> I use NTFS for shared partitions.  The ntfs-3g has worked very well for me and I have never had any data corruption.  Ubuntu and Windows also natively read/write for FAT32 partitions.  If you never have a file over 4GB then FAT32 is a good option.

BTW, ntfs-3g is default install on Ubuntu since Gutsy I believe.  Also NEVER use your /home or other Linux partitions as a shared partition, likewise DO NOT use ntfs-3g on your C:\ partition.  You are asking for trouble.  Make a separate partition for shared data.  There is never a need to write to C:\ in Windows from Linux or / in Linux from Windows.  The C:\ and / contain important system files that if inadvertently erased can cause that OS to be unusable.

See above - The OP wants to access the /home partition from windows - This CANNOT be done with a non-native *nix filesystem such as NTFS or FAT-anything

---

### Post by Calmor on 2008-12-18
> **dr.silly said:**
> I was really looking for native support but I looked at the ext2ifs software and I think I may try that out first. Has any one had any bad luck with that software?

I have another idea that may help you.

It sounds like you want access to all of the documents, music, videos, etc from both Windows and Linux.  I would caution that there is a lot more to your home folder than is regularly shown, and you could inadvertently change or delete important files.  *All* of your user-specific configuration files are in the home folder  In the best case, it would just look messy in Windows.

On my system, I have symlinked a folder with school documents into my home folder.  There's no reason why you couldn't do that with the entire My Documents folder in windows.  That way, you can access those files from both Windows and Ubuntu, not worry about setting up a new partition, and not affect your /home folder files from Windows.

Would you be interested in doing something like that?

---

### Post by jenkinbr on 2008-12-18
Brilliant!

+1 to that idea.

---

### Post by Calmor on 2008-12-19
> **jenkinbr said:**
> Brilliant!

+1 to that idea.

Thanks!

My reply was a little quick last night as I was short on time.  Today I'm at work and don't have my Ubuntu machine with me, but here's a brief rundown from memory:

The only downside to this that I can see is the default file structure.  Windows puts everything (music, videos, etc) nested into My Documents, whereas Ubuntu puts everything in the root of the user's folder.  If you follow these steps, you'll have a "Windows Documents" folder in your home folder, with the nested data folders just like Windows.  Some Linux programs (F-spot, for example) look for the Pictures folder inside the home folder, so you'll either have to do a lot of separate symlinks to keep the Ubuntu structure, or change the program settings to look in your new folders.

That said, make sure the Windows partition is mounted.  I believe in 32-bit Ubuntu this is done automatically, but in 64-bit, I had to modify fstab to do it at bootup.  If your Windows partition is mounted, it's most likely in /media/disk or something similar.  I will assume that's where it is for now, but your mileage may vary.

To symlink the entire My Documents folder into your home folder, you can do something like this in the terminal (note - /media/disk assumed to be the mount point of your Windows partition, and a default XP document structure is assumed - change as necessary, also replace <user> with your user names):

```
ls -s "/media/disk/Documents\ and\ Settings/<user>/My\ Documents" "/home/<user>/Windows\ Documents"
```

If your Windows folder is located in that location, this should have successfully placed a symbolic link in your home folder called "Windows Documents" which will look and act as if it were a normal Ubuntu folder, but contain everything from your Windows "My Documents" folder.  Any changes you make here will be seen in Windows.  You can change the name of the symlink to anything you want - "My Documents" etc - as long as that name is not already in use in that folder.  

If you want to keep the Ubuntu home folder layout, that is also possible.  As I mentioned, you can't symlink to an existing name, so you'll need to rename or remove the existing folders.  Then, follow the same general code as above:

```
ls -s "/media/disk/Documents\ and\ Settings/<user>/My\ Documents/My/ Videos" /home/<user>/Videos

ls -s "/media/disk/Documents\ and\ Settings/<user>/My\ Documents/My/ Music" /home/<user>/Music

ls -s "/media/disk/Documents\ and\ Settings/<user>/My\ Documents/My/ Pictures" /home/<user>/Pictures
```

The tricky one may be the "Documents" folder, as most people just load up the root "My Documents" folder in Windows.  You'll need to create a Documents folder in Windows and keep everything there.

I can't test the ln command right now, so I'm not 100% sure how it handles filenames with spaces - therefore I added the quotes.  They may not be necessary, or you may need to change it to a single quote instead, etc.  

After you do this one time, it will stay there, and you can delete the symbolic link without affecting any of the files in your Windows partition.

Hope that helps.  If you run into trouble or need a step-by-step breakdown, I can post back later today when I have my Ubuntu machines in front of me.

Edit: I should also caution that this uses the Windows partition for your files.  There's no problem with doing so, unless you plan to remove the Windows partition.  Before removing Windows completely, you will need to physically copy the files to the Ubuntu partition, else they will be lost.

---

